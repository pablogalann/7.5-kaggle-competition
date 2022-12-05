# Competición de Kaggle para Bootcamp de Data OCT'22:


## 📈OBJECTIVO

- Preparar los datos para los diversos modelos (proceso empírico) 
- Entrenar y Testear modelos de Machine Learning
- Subir los resultados con el mejor modelo entrenado de Machine Learning
- Hacer pull request con la presentación en la carpeta de 'PPTS' 
- Crear repo propio del proyecto (issue)


## 🧠 CARGA Y ANALISIS DE DATOS

1º Importación de datos a partir de los archivos Salaries_data.csv y Testeo.csv

2º Exploracion, limpieza y transformación:
      df.type() > Observamos columnas de tipo categorico: 'experience_level','employment_type','job_title','employee_residence','company_location, 'company_size'. 
      
3º Con el fin de nuestro modelo predictivo funcione, debemos convertir todos los datos en categoricos en numericos:
    Utilización de 2 metodos:
    - LabelEncoder(), Transforma cada uno de los datos categoricos en etiquetas numericas asociados a su peso dentro del df.
    - pd.get_dummies(), Transforma cada uno de los datos en etiquetas numericas binarias, entre 0 y 1.
    
* IMPORTANTE. Concatenar en un solo df, los dos dataframe que tenemos, para que el proceso de transformación a tipo numerico sea homogeneo

## 👉 DETERMINAMOS X y Y

1º Una vez todos los datos de nuestro dataframe son numericos, determinamos la X y la y, con el fin de hacer una predición sobre y.
2º Spliteamos x e y, para obtener un porcentaje de entreno y otro de test. 
    'X_train, X_test, y_train, y_test = tts(X, y, train_size=0.8, test_size=0.2, random_state=22)'
    
## 🤖 ELEGIMOS EL MODELO DE MACHINE LEARNING.

1º Utilizamos lazyregressor para tener una aproximacion de los modelos más optimos para nuestro caso.
    'reg = LazyRegressor(verbose=0, ignore_warnings=False, custom_metric=None)' 

2º GradientBoostingRegressor                                   
   RandomForestRegressor                                           
   BaggingRegressor
   
   Estos 3 modelos son los que previsiblemente nos arrojan un error más bajo, en pasos posteriores comprobaremos empiricamente
   cierto
   
## 🌲 RAMDOM FOREST REGRESSOR.
from sklearn.ensemble import RandomForestRegressor as Rfr

1º Iniciamos modelo; rfr = Rfr()   
2º Entrenamos modelo; rfr.fit(X_train, y_train)
3º Predecimos modelo; y_pred_train=rfr.predict(X_testeo) +++++ UTILIZAMOS LA MUESTRA DE TESTEO KAGGLE+++++++ len=107
4º Calculamos RMSE y RSE.
   'MSE = mean_squared_error(y_train, y_pred_train)'
   'RMSE = math.sqrt(MSE)'


## 🌪 GBR.
from sklearn.ensemble import GradientBoostingRegressor 

1º Iniciamos modelo; boo = GradientBoostingRegressor()   
2º Entrenamos modelo; boo.fit(X_train, y_train)
3º Predecimos modelo; y_pred_train=boo.predict(X_testeo) +++++ UTILIZAMOS LA MUESTRA DE TESTEO KAGGLE+++++++ len=107
4º Calculamos RMSE y RSE.
   'MSE = mean_squared_error(y_train, y_pred_train)'
   'RMSE = math.sqrt(MSE)'

## 🥇 ELEGIMOS LA MUESTRA MAS FAVORABLE Y LA CARGAMOS EN KAGGLE.

