# Estimación del nivel de estrés basada en la respuesta galvánica cutánea (GSR)

- Evelyn Marcela Caro Rodríguez - 5600848 - est.evelyn.caro@unimilitar.edu.co

- María Angel Benavides Silva - 5600852 - est.mariaa.benavides@unimilitar.edu.co


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
Para la captura de la señal galvánica se implementó el siguiente código, en el cual se evidencia lo siguiente:

```matlab
clear, clc, close all
if exist('b', 'var'), clear b; end
nombreDispositivo  = "ESP32_S3_GSR";
serviceUUID        = "6E400001-B5A3-F393-E0A9-E50E24DCCA9E";
characteristicUUID = "6E400003-B5A3-F393-E0A9-E50E24DCCA9E";
fs = 25; duracion = 60; alpha = 0.02; condicion = "Relajacion";
N = fs * duracion;
tiempo_baseline = 10;
N_baseline = tiempo_baseline * fs;
ref_scl = 0.10; ref_scr = 0.05; ref_eventos = 10; ref_pendiente = 0.002;
try
    b = ble(nombreDispositivo);
catch ME
    error('No se pudo establecer conexión BLE.');
end
c = characteristic(b, serviceUUID, characteristicUUID);
```

En esta Primera parte del codigo se  definen las credenciales necesarias para la conexión BLE, incluyendo los identificadores únicos de servicio y característica asociados al perfil Nordic UART. Con ello se habilita el canal de transmisión de datos entre MATLAB y la ESP32; En cuanto a la adquisición de la señal, se establece una frecuencia de muestreo de 25 Hz y una duración de 60 segundos, lo que corresponde a un total de 1500 muestras. Se incorpora un factor de suavizado para separar el componente tónico y se define la condición experimental, como relajación, estado normal o estres.

```matlab
while k <= N && toc < duracion
    dataRaw = read(c);
    ...
    scl_actual = alpha * volt + (1-alpha) * scl_actual;
    scr(k) = gsr(k) - scl(k);
    ...
end
dt = diff(t);
fs_real = 1 / mean(dt);
gsr_baseline = mean(gsr(1:N_baseline));
gsr_norm = gsr - gsr_baseline;
if gsr_promedio < 1.4
    nivel_estres = "RELAJADO";
elseif gsr_promedio >= 1.4 && gsr_promedio <= 1.7
    nivel_estres = "NORMAL";
else
    nivel_estres = "ESTRESADO";
end
scr_suave = movmean(scr, 5);
umbral_scr = 0.02; distancia_minima = round(fs_real); 
for k = 2:length(scr_suave)
    if scr_suave(k) >= umbral_scr && scr_suave(k-1) < umbral_scr ...
```

En la siguiente parte del código se aborda principalmente el procesamiento de la señal galvánica una vez recibida desde el microcontrolador. En primer lugar, se ejecuta un bucle controlado por el reloj interno que acumula las muestras capturadas. Los datos, transmitidos en forma de bytes, se convierten primero a texto y posteriormente a valores numéricos para su análisis.
Se aplica un filtro adaptativo exponencial que separa el componente tónico (SCL), correspondiente a la parte lenta y basal de la señal. A partir de ello se obtiene también el componente fásico (SCR), que refleja las variaciones rápidas asociadas a respuestas simpáticas. El algoritmo ajusta el número real de muestras recibidas y calcula la frecuencia efectiva de adquisición, compensando posibles variaciones de latencia en la transmisión inalámbrica.
Posteriormente, las señales se normalizan restando el voltaje medio inicial, de modo que las variaciones comiencen desde un nivel de referencia centrado en cero. Con esta base, se segmenta el estado autonómico en tres categorías: relajado, normal o estresado, según el nivel medio de conductancia. Además, se aplica un filtro de media móvil para reducir el ruido y se implementa un detector de eventos fisiológicos. Este detector identifica incrementos rápidos en la señal (flancos ascendentes) que superan un umbral definido y utiliza un período refractario de aproximadamente un segundo para evitar contabilizar varias veces el mismo evento.

```matlab
scl_max = max(scl);
scl_min = min(scl);
scl_promedio = mean(scl);

scr_max = max(scr);
scr_min = min(scr);
scr_promedio = mean(scr);
amplitud_scr = max(scr_suave) - min(scr_suave);

delta_scl = scl(end) - scl_baseline;
delta_gsr = gsr(end) - gsr_baseline;
max_delta_scl = max(scl_norm);
max_delta_gsr = max(gsr_norm);

std_gsr = std(gsr);
std_scl = std(scl);
std_scr = std(scr);

rms_gsr = rms(gsr);
rms_scl = rms(scl);
rms_scr = rms(scr);

coef_scl = polyfit(t,scl,1);
pendiente_scl = coef_scl(1);
variabilidad_scl = std(scl_norm);
delta_scl_promedio = mean(scl_norm);

puntaje_scl = min(max((max_delta_scl / ref_scl) * 100, 0), 100);
puntaje_scr = min(max((amplitud_scr / ref_scr) * 100, 0), 100);
puntaje_eventos = min(max((numero_eventos_scr / ref_eventos) * 100, 0), 100);
puntaje_pendiente = min(max((abs(pendiente_scl) / ref_pendiente) * 100, 0), 100);

indice_estres = 0.50 * puntaje_scl + 0.25 * puntaje_scr + 0.15 * puntaje_eventos + 0.10 * puntaje_pendiente;
indice_estres = min(max(indice_estres,0),100);
indice_relajacion = 100 - indice_estres;

fprintf('\n=====================================\n')
fprintf('       EVALUACIÓN DEL ESTADO\n')
fprintf('=====================================\n')
fprintf('Condición:               %s\n', condicion)
fprintf('GSR Promedio:            %.4f V\n', gsr_promedio)
fprintf('Estado Diagnosticado:   %s\n', nivel_estres)
fprintf('=====================================\n\n')

if nivel_estres == "ESTRESADO"
    disp("  ALERTA: LA PERSONA ESTÁ ESTRESADA (> 1.7 V) ")
    
    % Generar tono de alarma (Frecuencia: 1000 Hz por 1.5 segundos)
    fs_audio = 8000;
    t_audio = 0:1/fs_audio:1.5;
    frecuencia_alarma = 1000;
    tono = sin(2*pi*frecuencia_alarma*t_audio);
    
    sound(tono, fs_audio); % Reproducir tono
elseif nivel_estres == "NORMAL"
    disp(" Nivel de estrés dentro del rango normal (1.4 V - 1.7 V).")
else
    disp(" Persona completamente relajada (< 1.4 V).")
end

fprintf('\n=====================================\n')
fprintf('           MÉTRICAS GSR\n')
fprintf('=====================================\n')
fprintf('\n--- SEÑAL GSR ---\n')
fprintf('GSR máximo:              %.4f V\n',gsr_max)
fprintf('GSR mínimo:              %.4f V\n',gsr_min)
fprintf('GSR promedio:            %.4f V\n',gsr_promedio)
fprintf('GSR desviación estándar %.4f V\n',std_gsr)
fprintf('GSR RMS:                 %.4f V\n',rms_gsr)
fprintf('\n--- SCL ---\n')
fprintf('SCL basal:               %.4f V\n',scl_baseline)
fprintf('SCL máximo:              %.4f V\n',scl_max)
fprintf('SCL mínimo:              %.4f V\n',scl_min)
fprintf('SCL promedio:            %.4f V\n',scl_promedio)
fprintf('SCL desviación estándar %.4f V\n',std_scl)
fprintf('SCL RMS:                 %.4f V\n',rms_scl)
fprintf('Pendiente SCL:           %.6f V/s\n',pendiente_scl)
fprintf('Variabilidad SCL:        %.4f V\n',variabilidad_scl)
fprintf('Cambio SCL promedio:     %.4f V\n',delta_scl_promedio)
fprintf('\n--- CAMBIO SCL ---\n')
fprintf('Cambio final SCL:        %.4f V\n',delta_scl)
fprintf('Máximo cambio SCL:       %.4f V\n',max_delta_scl)
fprintf('\n--- SCR ---\n')
fprintf('SCR máximo:              %.4f V\n',scr_max)
fprintf('SCR mínimo:              %.4f V\n',scr_min)
fprintf('SCR promedio:            %.4f V\n',scr_promedio)
fprintf('SCR amplitud:            %.4f V\n',amplitud_scr)
fprintf('SCR desviación estándar %.4f V\n',std_scr)
fprintf('SCR RMS:                 %.4f V\n',rms_scr)
fprintf('Eventos SCR:             %d\n',numero_eventos_scr)
fprintf('\n--- CAMBIO GSR ---\n')
fprintf('Cambio final GSR:        %.4f V\n',delta_gsr)
fprintf('Máximo cambio GSR:       %.4f V\n',max_delta_gsr)
fprintf('\n--- PUNTAJES ---\n')
fprintf('Puntaje SCL:             %.2f / 100\n',puntaje_scl)
fprintf('Puntaje SCR:             %.2f / 100\n',puntaje_scr)
fprintf('Puntaje eventos:         %.2f / 100\n',puntaje_eventos)
fprintf('Puntaje pendiente:       %.2f / 100\n',puntaje_pendiente)
fprintf('\n--- ÍNDICES FINALES ---\n')
fprintf('NIVEL:                   %s\n',nivel_estres)
fprintf('=====================================\n')


figure('Name','Señal GSR','NumberTitle','off')
subplot(3,1,1)
plot(t,gsr,'LineWidth',1.2)
grid on
xlabel('Tiempo [s]')
ylabel('Voltaje [V]')
title(['Señal GSR adquirida - ' condicion])
xlim([0 duracion])

subplot(3,1,2)
plot(t,scl,'LineWidth',1.3)
hold on
yline(scl_baseline,'--')
grid on
xlabel('Tiempo [s]')
ylabel('Voltaje [V]')
title('Componente SCL - Nivel basal')
legend('SCL','Baseline')
xlim([0 duracion])

subplot(3,1,3)
plot(t,scr,'LineWidth',0.8)
hold on
plot(t,scr_suave,'LineWidth',1.5)
yline(umbral_scr,'--')
grid on
xlabel('Tiempo [s]')
ylabel('Voltaje [V]')
title('Componente SCR - Respuesta rápida')
legend('SCR original','SCR suavizado','Umbral')
xlim([0 duracion])

figure('Name','Señales Normalizadas','NumberTitle','off')
subplot(2,1,1)
plot(t,gsr_norm,'LineWidth',1.3)
hold on
yline(0,'--')
grid on
xlabel('Tiempo [s]')
ylabel('\Delta Voltaje [V]')
title(['GSR respecto al nivel basal - ' condicion])
xlim([0 duracion])

subplot(2,1,2)
plot(t,scl_norm,'LineWidth',1.5)
hold on
yline(0,'--')
grid on
xlabel('Tiempo [s]')
ylabel('\Delta Voltaje [V]')
title(['SCL respecto al nivel basal - ' condicion])
xlim([0 duracion])

figure('Name','Detección de respuestas SCR','NumberTitle','off')
plot(t,scr_suave,'LineWidth',1.3)
hold on
yline(umbral_scr,'--')
if ~isempty(eventos_scr)
    plot(t(eventos_scr), scr_suave(eventos_scr), 'o', 'MarkerSize',7, 'LineWidth',1.5)
    legend('SCR suavizado','Umbral','Eventos SCR')
else
    legend('SCR suavizado','Umbral')
end
grid on
xlabel('Tiempo [s]')
ylabel('SCR [V]')
title(['Respuestas SCR detectadas - ' condicion])
xlim([0 duracion])

figure('Name','Estado de Estrés GSR','NumberTitle','off')
axis off
text(0.5,0.70,...
    sprintf('GSR PROMEDIO\n\n%.2f V', gsr_promedio),...
    'HorizontalAlignment','center','FontSize',22,'FontWeight','bold')

if nivel_estres == "ESTRESADO"
    color_texto = 'r';
elseif nivel_estres == "NORMAL"
    color_texto = [0.9 0.5 0];
else
    color_texto = 'g';
end

text(0.5,0.30,...
    nivel_estres,...
    'HorizontalAlignment','center','FontSize',30,'FontWeight','bold','Color',color_texto)

figure('Name','Componentes del Índice de Activación','NumberTitle','off')
puntajes = [puntaje_scl puntaje_scr puntaje_eventos puntaje_pendiente];
bar(puntajes)
grid on
ylim([0 100])
ylabel('Puntaje [0-100]')
title('Componentes utilizados para calcular el índice')
xticklabels({'SCL','SCR','Eventos','Pendiente SCL'})

figure('Name','Relajación y Activación','NumberTitle','off')
valores = [indice_relajacion indice_estres];
bar(valores)
grid on
ylim([0 100])
ylabel('Índice [0-100]')
title('Índice de Relajación vs Índice de Activación')
xticklabels({'Relajación','Activación'})

if condicion == "Relajacion"
    nombre_mat = "GSR_Relajacion.mat";
    nombre_csv = "GSR_Relajacion.csv";
else
    nombre_mat = "GSR_Hiperventilacion.mat";
    nombre_csv = "GSR_Hiperventilacion.csv";
end

save(nombre_mat,...
     "t","gsr","scl","scr","scr_suave","gsr_norm","scl_norm",...
     "fs","fs_real","gsr_baseline","scl_baseline","delta_gsr","delta_scl",...
     "delta_scl_promedio","max_delta_gsr","max_delta_scl","numero_eventos_scr",...
     "gsr_max","gsr_min","gsr_promedio","scl_max","scl_min","scl_promedio",...
     "scr_max","scr_min","scr_promedio","amplitud_scr","std_gsr","std_scl",...
     "std_scr","variabilidad_scl","rms_gsr","rms_scl","rms_scr","pendiente_scl",...
     "puntaje_scl","puntaje_scr","puntaje_eventos","puntaje_pendiente",...
     "indice_estres","indice_relajacion","nivel_estres","condicion")

writematrix([t gsr scl scr], nombre_csv)

disp(" ")
disp("=====================================")
disp("          DATOS GUARDADOS")
disp("=====================================")
fprintf("MAT: %s\n",nombre_mat)
fprintf("CSV: %s\n",nombre_csv)
fprintf("GSR Promedio: %.4f V\n",gsr_promedio)
fprintf("Estado final: %s\n",nivel_estres)
disp(" ")
disp("Prueba finalizada correctamente.")
```

Esta ultima parte del código se centra en el análisis final de la señal galvánica y en la generación de resultados. En primer lugar, se ajusta un modelo lineal de primer orden sobre la curva tónica (SCL) para estimar la pendiente, la cual refleja la tendencia temporal de la sudoración. Asimismo, se calculan métricas estadísticas como la desviación estándar y el valor eficaz (RMS), útiles para cuantificar la energía de la señal.
A partir de estos valores se normalizan cuatro parámetros clave en una escala porcentual y se integran en un índice global mediante un promedio ponderado: la variación máxima de la componente lenta, la amplitud de la rápida, la frecuencia de eventos electrodérmicos y la pendiente de la SCL. El complemento de este índice se interpreta como un indicador de relajación.
Finalmente, el programa imprime en consola un resumen ejecutivo del ensayo y, en caso de que el estado se clasifique como “estresado”, emite una señal acústica de advertencia a través de la tarjeta de sonido. Además, genera diversas representaciones gráficas: desde la visualización de la señal cruda y sus componentes, hasta diagramas de barras que muestran el aporte porcentual de cada parámetro y la clasificación codificada por colores (verde, naranja o rojo).


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

## CONCLUSIONES 

En conclusión, se logró desarrollar un código funcional que cumple con los objetivos planteados, a pesar de no contar aún con la capacidad de graficar en tiempo real. Este aspecto representa una oportunidad de mejora, ya que la incorporación de visualización continua permitiría un registro más dinámico y detallado de la señal.

Respecto al dispositivo vestible, se identifican posibles optimizaciones mediante pequeños ajustes en su estructura, lo que podría incrementar su comodidad y eficiencia. En cuanto al código, además de la transmisión inalámbrica que funciona de manera adecuada y estable, se sugiere implementar mejoras orientadas a la adquisición en tiempo real y al registro continuo de datos.

Los resultados obtenidos se reflejan en las gráficas generadas, donde se evidencian claramente estados de relajación y de estrés, lo que confirma la validez del sistema para diferenciar condiciones autonómicas.

El sistema desarrollado nos permitio confirmar los fundamentos teóricos expuestos sobre la actividad electrodérmica. Las pruebas que se realizaron evidenciaron la capacidad del dispositivo para capturar la activación del sistema nervioso simpático. La transición de un estado de relajación basal (con un índice de relajación de ~95 y voltaje cercano a 0.03 V sobre la línea base) a un estado de activación o estrés debido al susto geneado (con un índice de activación de ~40 y picos de hasta 3 V) valida la sensibilidad del sensor para detectar cambios autonómicos súbitos mediados por la secreción de las glándulas ecrinas.

La captura de datos de manera inalámbrica mediante el uso de ESP32-S3 garantizó una buena captura de datos,permitiendo además la movilidad necesaria para las tecnologías portátiles (wearables). Adicionalmente, la implementación de la alerta al superar el umbral de estrés (> 1.7 V) es de gran ayuda ya que permite la intervención de autorregulación inmediata frente a situaciones de sobrecarga cognitiva o emocional en la vida cotidiana.


## Bibliografía
[1] R. Singh, A. Gehlot, R. Saxena, K. Alsubhi, D. Anand, I. D. Noya, S. V. Akram, and S. Choudhury, “Stress Detector Supported Galvanic Skin Response System with IoT and LabVIEW GUI,” Computers, Materials & Continua, vol. 74, no. 1, 2023, doi: 10.32604/cmc.2023.023894.

[2] R. Markiewicz, A. Markiewicz-Gospodarek, and B. Dobrowolska, “Galvanic Skin Response Features in Psychiatry and Mental Disorders: A Narrative Review,” International Journal of Environmental Research and Public Health, vol. 19, no. 20, Art. no. 13428, 2022, doi: 10.3390/ijerph192013428.

[3] D. S. Bari, M. N. S. Rammoo, H. Y. Y. Aldosky, M. K. Jaqsi, and Ø. G. Martinsen, “The Five Basic Human Senses Evoke Electrodermal Activity,” Sensors, vol. 23, no. 19, p. 8181, Sep. 2023, doi: 10.3390/s23198181.

[4] M. Viqueira Villarejo, B. García Zapirain, and A. Méndez Zorrilla, “A Stress Sensor Based on Galvanic Skin Response (GSR) Controlled by ZigBee,” Sensors, vol. 12, pp. 6075–6101, May 2012, doi: 10.3390/s120506075.
