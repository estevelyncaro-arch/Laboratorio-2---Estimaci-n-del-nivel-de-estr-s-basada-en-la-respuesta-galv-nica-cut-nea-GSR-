# Estimación del nivel de estrés basada en la respuesta galvánica cutánea (GSR)

## Parte A 

La actividad electrodérmica tambien conocida como respuesta galvánica de la piel (GSR), abarca todas las propiedades eléctricas activas y pasivas observadas en la piel. Desde el punto de vista fisiológico, el GSR actúa como un marcador directo de la actividad del sistema nervioso autónomo simpático; la variación en la conductividad eléctrica cutánea está regulada por las glándulas sudoríparas ecrinas, localizadas en las regiones palmar y plantar principalmente, las cuales son controladas por los nervios sudomotores del sistema simpático a través de neurotransmisores como la acetilcolina y la noradrenalina. Cuando el sistema simpático se activa por estímulos térmicos o psicológicos, la secreción de sudor (rico en agua y electrolitos) llena los conductos sudoríparos y humecta el estrato córneo altamente resistivo, creando vías de transporte iónico que reducen la resistencia cutánea y elevan de manera transitoria la conductancia.

La generación de señales electrodérmicas está compuesta por estructuras cerebrales que regulan la activación simpática, incluyendo la corteza premotora, el hipotálamo, la formación reticular y, en particular, el sistema límbico (que comprende el hipocampo, la amígdala, los núcleos anteriores del tálamo y los cuerpos mamilares). El sistema límbico es importante al ser el responsable principal de las emociones, la motivación y el aprendizaje. La interacción entre el tálamo y el sistema límbico garantiza el funcionamiento idóneo del eje Amígdala-Hipotálamo-Pituitaria-Adrenal (AHPA), el cual rige las respuestas neurofisiológicas ante el estrés. Alteraciones en este eje se traducen clínicamente en disfunciones cognitivas, rumiaciones, insomnio, ansiedad y depresión. Como reflejo de esta actividad cerebral, el GSR se evalúa en dos componentes principales: el componente tónico, que representa fluctuaciones lentas asociadas a condiciones ambientales y de hidratación basal (como el nivel de conductancia de la piel, SCL); y el componente fásico, caracterizado por respuestas rápidas (como la respuesta de conductancia de la piel, SCR) evocadas directamente por ráfagas sudomotoras desencadenadas por estímulos discretos o de carga cognitiva.

Los cinco sentidos (vista, oído, tacto, gusto y olfato) también actúan como un desencadenante directo de la actividad electrodérmica, evidenciando el acoplamiento entre el procesamiento de la información sensorial y la carga cognitiva que activa el sistema simpático. Investigaciones experimentales simultáneas de parámetros fásicos (como la conductancia SCR, la susceptancia SSR y el potencial SPR) revelan que el organismo reacciona con diferente intensidad según el tipo de receptor activado, se ha demostrado que los estímulos químicos (gusto y olfato), producen mayores amplitudes fásicas que los estímulos físicos (vista, oído y tacto). El sentido del olfato genera respuestas electrodérmicas caracterizadas por amplitudes significativamente mayores en todos los parámetros y mayores tiempos de subida de la conductancia. Lo que se debe a la extrema sensibilidad del sistema olfatorio y a la transmisión directa e inmediata de impulsos desde las neuronas receptoras olfativas hacia las estructuras cerebrales.

Para la aplicación práctica de estos conceptos los sistemas de adquisición de datos biomédicos traducen la resistencia de la piel a variaciones de voltaje analógico empleando un circuito de divisor de tensión. Bajo el principio de la ley de Ohm, la tensión de salida de este circuito es inversamente proporcional a la resistencia de la piel: a medida que el paciente experimenta estrés o activación simpática, la sudoración aumenta, la resistencia cutánea disminuye y el voltaje de salida se eleva. Mediante análisis matemáticos de histogramas aplicados sobre estas señales digitalizadas, se han establecido los siguientes umbrales de clasificación fisiológica de voltaje para determinar de manera objetiva el nivel de tensión del usuario:
- Estado de Relajación: Se identifica cuando el voltaje medido por el dispositivo GSR es menor a 1.75 V
- Estado Normal: Se establece cuando las lecturas se sitúan en un rango intermedio entre 1.44 V y 1.75
- Estado de Estrés: Se determina cuando la tensión registrada supera el límite de 1.44 V, producto de la caída drástica de la resistencia de la piel debido al incremento en la actividad de las glándulas sudoríparas

La parametrización cuantitativa de estos estados fisiológicos proporciona una base sólida para que las tecnologías portátiles, integradas con sistemas de Internet y conectividad inalámbrica, envíen alertas en tiempo real y permitan una intervención de autorregulación inmediata frente a situaciones de sobrecarga cognitiva o emocional en la vida cotidiana.

##
<img width="591" height="1280" alt="image" src="https://github.com/user-attachments/assets/32741961-999a-458e-b983-6cefb6c740ae" />  <img width="591" height="1280" alt="image" src="https://github.com/user-attachments/assets/363abe7b-a6f7-40a6-86a5-c2e09f93d3c0" />  <img width="591" height="1280" alt="image" src="https://github.com/user-attachments/assets/58fff02b-dc04-4f51-92bd-11546a246ee8" />


## Parte B



## Parte C
Inicialmente se realiza la captura de la señal mientras el paciente se encuentra en relajación, observando que en los gráficos obtenidos la señal se encuentra al rededor, o cerca al nivel basal, obteniendo un promedio de 0.03 Voltios (V).

<img width="1600" height="747" alt="image" src="https://github.com/user-attachments/assets/619dc8f0-d076-4d8c-a83d-8a4fb33b92d8" />

<img width="1600" height="695" alt="image" src="https://github.com/user-attachments/assets/cace1e0a-a6e3-4160-a257-a460efbbd017" />

##

Adicionalmente se toma la captura de la señal en relajación como se realizo anteriormente, sin embargo durante esta captura el paciente presenta un susto, lo que genera "Estrés", pasando de un estado de relajación en aproximadamente 0.03 V a un estado de estres elevando el voltaje a aproximadamente 3 V, como se puede evidenciar en los siguientes gráficos.

<img width="1600" height="714" alt="image" src="https://github.com/user-attachments/assets/fa7c8d9b-4262-466e-b7d4-6ebf0d100938" />

<img width="1600" height="749" alt="image" src="https://github.com/user-attachments/assets/f7afc8bc-c730-42cf-8dcc-b52504a8e00d" />

##

Finalmente obtenemos tres gráficos importantes que se explican a continuación.

- En el primer gráfico correspondiente a la primer señal obtenida, observamos que el índice de relajación tiene un nivel alto siendo un valor al redero de 95, así mismo se observa que la activación es muy pequeña con un indice de 5 aporximadamente, confirmando que el paciente se encuentra en un estado de relajación.
  
<img width="1600" height="742" alt="image" src="https://github.com/user-attachments/assets/18924cc6-0091-455c-b13b-61e30bc3fa8f" />

- Para el seundo gráfico correspondiente al estímulo de estrés, se evidencia que el nivel de relajación disminuye significativamente reduciendo su índice a 60, y aumentando el índice de la activación a 40 aproximadamete, mostrando el aumento del nivel de estres.
  
<img width="1600" height="768" alt="image" src="https://github.com/user-attachments/assets/60027c9c-6391-4905-b6de-0cd4e5b679a8" />

- Finalmente se tiene el siguiente gráfico correspondiente a el estímulo de estrés donde se evidencia que el nivel de conductancia aumenta, siendo uno de los componentes relevantes para establecer los indices de relajación y activación.

<img width="1600" height="745" alt="image" src="https://github.com/user-attachments/assets/12b0fa0a-3387-4c7d-9f15-077f6c7dd669" />


## Bibliografía
[1] R. Singh, A. Gehlot, R. Saxena, K. Alsubhi, D. Anand, I. D. Noya, S. V. Akram, and S. Choudhury, “Stress Detector Supported Galvanic Skin Response System with IoT and LabVIEW GUI,” Computers, Materials & Continua, vol. 74, no. 1, 2023, doi: 10.32604/cmc.2023.023894.

[2] R. Markiewicz, A. Markiewicz-Gospodarek, and B. Dobrowolska, “Galvanic Skin Response Features in Psychiatry and Mental Disorders: A Narrative Review,” International Journal of Environmental Research and Public Health, vol. 19, no. 20, Art. no. 13428, 2022, doi: 10.3390/ijerph192013428.

[3] D. S. Bari, M. N. S. Rammoo, H. Y. Y. Aldosky, M. K. Jaqsi, and Ø. G. Martinsen, “The Five Basic Human Senses Evoke Electrodermal Activity,” Sensors, vol. 23, no. 19, p. 8181, Sep. 2023, doi: 10.3390/s23198181.

[4] M. Viqueira Villarejo, B. García Zapirain, and A. Méndez Zorrilla, “A Stress Sensor Based on Galvanic Skin Response (GSR) Controlled by ZigBee,” Sensors, vol. 12, pp. 6075–6101, May 2012, doi: 10.3390/s120506075.
