library(qcc)
library(plotly)
library(htmlwidgets)

# Filter data for Machine 1 and select PartLength
machine1_partlength <- X002..1.$PartLength[X002..1.$Machine == 1]

n_samples <- length(machine1_partlength)
subgroup_size <- 5
num_subgroups <- floor(n_samples / subgroup_size)
partlength_matrix <- matrix(machine1_partlength[1:(num_subgroups * subgroup_size)], ncol = subgroup_size, byrow = TRUE)

# Create an x-bar control chart for PartLength
partlength_qcc <- qcc(partlength_matrix, type = "xbar", confidence.level = 0.9973)

# Function to plot qcc object with plotly
plot_qcc <- function(qcc_object, title_text, y_axis_label) {
  data_df <- data.frame(Sample = 1:length(qcc_object$statistics), Value = qcc_object$statistics)
  cl <- qcc_object$limits[1]
  lcl <- qcc_object$limits[2]
  ucl <- qcc_object$limits[3]
  p <- plot_ly(data_df, x = ~Sample, y = ~Value, type = 'scatter', mode = 'lines+markers', name = 'Subgroup Mean') %>%
    add_trace(y = cl, mode = 'lines', name = 'CL', line = list(color = '#0072B2', dash = 'solid')) %>%
    add_trace(y = lcl, mode = 'lines', name = 'LCL', line = list(color = '#D55E00', dash = 'dash')) %>%
    add_trace(y = ucl, mode = 'lines', name = 'UCL', line = list(color = '#D55E00', dash = 'dash')) %>%
    layout(title = list(text = title_text, font = list(size = 18)),
           xaxis = list(title = list(text = 'Subgroup Number', font = list(size = 18)), tickfont = list(size = 14)),
           yaxis = list(title = list(text = y_axis_label, font = list(size = 18)), tickfont = list(size = 14)),
           plot_bgcolor = 'white', paper_bgcolor = 'white')
  return(p)
}

partlength_plot <- plot_qcc(partlength_qcc, "X-bar Chart for PartLength (Machine 1)", "PartLength (mm)")

# Save the plot as an HTML widget
saveWidget(partlength_plot, file = "media/plots/partlength_xbar_machine1.html", selfcontained = TRUE)

# Print a summary of the control chart
print(summary(partlength_qcc))
