library(stringr)
library(stringi)

normalizar_texto <- function(x) {
  x %>%
    tolower() %>%
    stringi::stri_trans_general("Latin-ASCII")
}

clasificar_area <- function(fila, areas) {
  
  texto <- normalizar_texto(paste(fila, collapse = " "))
  
  conteos <- sapply(areas, function(palabras) {
    sum(str_detect(texto, palabras))
  })
  
  max_coincidencias <- max(conteos)
  
  if (max_coincidencias == 0) {
    return("Sin clasificación")
  }
  
  areas_max <- names(conteos[conteos == max_coincidencias])
  paste(areas_max, collapse = "; ")
}