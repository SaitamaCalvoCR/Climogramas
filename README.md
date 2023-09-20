# Instalación de paquetes
#| label: datatable
#| warning: false
# Paquetes y librerías
install.packages("ggplot2")
install.packages("ggmap")
library(ggplot2)
library(ggmap)
library(leaflet)

# Datos de Bengazhi
#| label: datatable
#| warning: false
datos_clima <- data.frame(
  Mes = 1:12,  # Meses de enero a diciembre
  Precipitaciones = c(23, 23, 22, 19, 16, 14, 13, 13, 14, 17, 19, 22),  # Precipitación en mm
  Temperatura = c(0.8, 1, 2, 4.3, 13, 18, 17, 14.5, 8.6, 5.6, 2, 1.3)  # Temperatura en °C
)

# Crear el climograma
#| label: datatable
#| warning: false
climograma <- ggplot(datos_clima, aes(x = Mes)) +
  geom_col(aes(y = Temperatura, fill = "Temperatura"), width = 0.5) +
  geom_line(aes(y = Precipitaciones, group = 1, color = "Precipitación"), size = 1) +
  
  # Personalizar colores de el climograma
  #| label: datatable
  #| warning: false
  scale_fill_manual(values = "aquamarine1", name = "Temperatura") +
  scale_color_manual(values = "red2", name = "Precipitación") +
  
  # Personalización del tema
  #| label: datatable
  #| warning: false
  theme_minimal() +
  theme(legend.position = "top", legend.title = element_text(size = 12)) +
  
  # Nombres de los meses
  #| label: datatable
  #| warning: false
  scale_x_continuous(
    breaks = 1:12,
    labels = c("Ene", "Feb", "Mar", "Abr", "May", "Jun", "Jul", "Ago", "Sep", "Oct", "Nov", "Dic"),
    name = "Mes"
  )

# Imprimir el climograma
print(climograma)
