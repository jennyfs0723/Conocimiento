# Conocimiento
Stored Procedure y Views
DESCRIPCION DEL PROYECTO: 
"LogiTrans es un sistema de gestión logística diseñado para registrar envíos, asignar rutas óptimas, verificar disponibilidad de conductores y vehículos, y analizar estadísticas de tiempos, costos e incidencias. El proyecto busca optimizar la operación de transporte y brindar información clara para la toma de decisiones."

INSTRUCCIONES DE USO:
1. Ejecutar el script en MySQL para crear las tablas, vistas y procedimientos.
2. Insertar los seeders.
Usar los procedimientos almacenados:
1.CALL registrar_envio(...) para registrar un nuevo envío.
2.CALL AsignarRutaOptima('numero_guia') para asignar la mejor ruta.
3.CALL AsignarVehiculoConductor(envioID, @conductor, @vehiculo) para asignar vehiculo y conductor de acuerdo a disponibilidad.
4.CALL RegistrarSeguimientoEnvio(...) Para actualizar el seguimiento de envio
5.CALL ProgramarMantenimientoFlota(idvehiculo,km) si el vehiculo ha cumplido mas de 10.000 km se programa mantenimiento
Consultar las vistas para obtener estadísticas:
1.SELECT * FROM vw_EnviosEnCurso; -- para observar que envios estan en transito
2.SELECT * FROM vw_DisponibilidadFlota WHERE zona_geografica = 'medellin norte'; -- disponibilidad por tipo de vehiulo y zona
3.SELECT conductorID,total_entregas,CONCAT(ROUND(promedio_horas_entrega, 2), ' horas') AS promedio_horas_entrega FROM vw_RendimientoConductores ORDER BY promedio_horas_entrega ASC; -- Estadísticas de rendimiento de conductores por tiempo y entregas.
4.SELECT * FROM vw_EstadisticasRutas ORDER BY promedio_horas_entrega ASC; -- Análisis de tiempos y costos por ruta.
5.SELECT * FROM vw_IncidenciasTransporte; -- registro de incidencias por tipo de vehiculo y zona

ESTRUCTURA DE LOS MODULOS IMPLEMENTADOS:
Módulo de Envíos = registrar_envio, vw_EnviosEnCurso.
Módulo de Rutas = AsignarRutaOptima, vw_EstadisticasRutas.
Módulo de Conductores/Vehículos = AsignarVehiculoConductor, vw_DisponibilidadFlota.
Módulo de Seguimiento = RegistrarSeguimientoEnvio, vw_RendimientoConductores.
Módulo de Incidencias = vw_IncidenciasTransporte.
Módulo de Mantenimiento = ProgramarMantenimientoFlota.

