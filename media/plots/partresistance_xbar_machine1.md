library(qcc)
library(plotly)
library(htmlwidgets)

# Filter data for Machine 1 and select PartResistance
machine1_partresistance <- X002..1.$PartResistance[X002..1.$Machine == 1]

n_samples_res <- length(machine1_partresistance)
subgroup_size_res <- 5
num_subgroups_res <- floor(n_samples_res / subgroup_size_res)
partresistance_matrix <- matrix(machine1_partresistance[1:(num_subgroups_res * subgroup_size_res)], ncol = subgroup_size_res, byrow = TRUE)

# Create an x-bar control chart for PartResistance
partresistance_qcc <- qcc(partresistance_matrix, type = "xbar", confidence.level = 0.9973)

# Function to plot qcc object with plotly (assuming plot_qcc is defined elsewhere or in this script)
# plot_qcc function definition would go here if not globally available, for brevity it's omitted as it was defined in the previous R cell.
partresistance_plot <- plot_qcc(partresistance_qcc, "X-bar Chart for PartResistance (Machine 1)", "PartResistance (Ohms)")

# Save the plot as an HTML widget
saveWidget(partresistance_plot, file = "media/plots/partresistance_xbar_machine1.html", selfcontained = TRUE)

# Print a summary of the control chart
print(summary(partresistance_qcc))
