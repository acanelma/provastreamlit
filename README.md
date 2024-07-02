import streamlit as st
import pandas as pd
import plotly.express as px

def main():
    st.title("Aprendamos sobre la Coagulación")
    
    st.write("Bienvenidos a nuestra aplicación interactiva para entender la coagulación.")
    
    # Sección 1: Introducción
    st.header("¿Qué es la coagulación?")
    st.write("La coagulación es el proceso por el cual la sangre cambia de líquida a gel, formando un coágulo. Es crucial para detener el sangrado cuando nos lastimamos.")
    
    # Sección 2: Pasos de la coagulación
    st.header("Pasos de la coagulación")
    steps = [
        "1. Lesión del vaso sanguíneo",
        "2. Contracción del vaso",
        "3. Adhesión de plaquetas",
        "4. Activación de factores de coagulación",
        "5. Formación de fibrina",
        "6. Estabilización del coágulo"
    ]
    step = st.selectbox("Selecciona un paso para aprender más:", steps)
    
    if step == steps[0]:
        st.write("Cuando un vaso sanguíneo se daña, se exponen tejidos que normalmente no están en contacto con la sangre.")
    elif step == steps[1]:
        st.write("El vaso sanguíneo se contrae para reducir el flujo de sangre al área dañada.")
    elif step == steps[2]:
        st.write("Las plaquetas se adhieren al sitio de la lesión, formando un tapón plaquetario inicial.")
    elif step == steps[3]:
        st.write("Se activan proteínas especiales llamadas factores de coagulación, iniciando una cascada de reacciones.")
    elif step == steps[4]:
        st.write("Se forma una proteína llamada fibrina, que crea una red para atrapar más plaquetas y células sanguíneas.")
    else:
        st.write("El coágulo se estabiliza y se fortalece para detener completamente el sangrado.")

    # Sección 3: Factores de coagulación
    st.header("Factores de coagulación")
    factors = pd.DataFrame({
        'Factor': ['I', 'II', 'III', 'IV', 'V', 'VII', 'VIII', 'IX', 'X', 'XI', 'XII', 'XIII'],
        'Nombre': ['Fibrinógeno', 'Protrombina', 'Tromboplastina tisular', 'Calcio', 'Proacelerina', 'Proconvertina', 'Factor antihemofílico A', 'Factor antihemofílico B', 'Factor Stuart-Prower', 'Antecedente tromboplastínico del plasma', 'Factor Hageman', 'Factor estabilizador de fibrina']
    })
    
    st.dataframe(factors)
    
    selected_factor = st.selectbox("Selecciona un factor para ver su importancia:", factors['Factor'])
    
    # Aquí podrías añadir información específica sobre cada factor
    
    # Sección 4: Visualización interactiva
    st.header("Visualización de la cascada de coagulación")
    # Esto es un ejemplo simplificado. En una aplicación real, se crearía una visualización más detallada.
    cascade_data = pd.DataFrame({
        'Paso': ['Lesión', 'Plaquetas', 'Factores', 'Fibrina', 'Coágulo'],
        'Tiempo': [0, 1, 2, 3, 4],
        'Intensidad': [10, 30, 60, 80, 100]
    })
    
    fig = px.line(cascade_data, x='Tiempo', y='Intensidad', text='Paso')
    st.plotly_chart(fig)
    
    # Sección 5: Quiz interactivo
    st.header("¡Pon a prueba tus conocimientos!")
    question = st.radio(
        "¿Cuál es el último paso en la formación de un coágulo?",
        ("Adhesión de plaquetas", "Formación de fibrina", "Estabilización del coágulo")
    )
    
    if question == "Estabilización del coágulo":
        st.success("¡Correcto! La estabilización del coágulo es el paso final en el proceso de coagulación.")
    else:
        st.error("Esa no es la respuesta correcta. Inténtalo de nuevo.")

if __name__ == "__main__":
    main()
