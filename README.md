# Quantum-Monte-Carlo.
import numpy as np
import matplotlib.pyplot as plt 

def make_gauss(sig, mu): #  Define una funcion que depende de sigma y mu, debemos tener en cuenta que mu=0. 
    return lambda x: 1/(sig * (2*np.pi)**.5) * np.e ** (-(x-mu)**2/(2 * sig**2)) # función densidad de probabilidad

def main(): # Define los datos para el gráfico
    ax = plt.figure().add_subplot(1,1,1)
    x = np.arange(-4, 4, 0.01) # Rango para el eje x
    sigm = np.sqrt([0.1 , 0.2, 0.5 , 1, 5.0, 20]) # s=valores que toma σ², 
    mu1 = [0, 0, 0, 0, 0 ] # tomando a mu=0. La distribución gaussiana es simétrica alrededor de $\mu$. 
    color1 = ['m','b','c','g', 'y' ]  #colores de las diferentes gráficas

    for sig, mu, color in zip(sigm, mu1, color1): 
        gauss = make_gauss(sig, mu)(x)
        ax.plot(x, gauss, color, linewidth=2)

    plt.xlim(-4, 4) #límite en x para el gráfico
    plt.xlabel("x") # Nombra el eje x
    plt.ylim(0, 1.5) #límite en y para el gráfico
    plt.ylabel("f(x)") # Me nombra el eje y
    plt.title("Función Densidad de Probabilidad f(x)")
    plt.legend([' $\sigma²: 0.1$', ' $\sigma² : 0.2$', '$\sigma² : 0.5$',  '$\sigma²: 1.0$', '$\sigma²: 5.0$'], loc='best')
    plt.savefig('PDF.png') #Me guarda la imagen en formato .png
    plt.savefig('PDF.pdf') #Me guarda la imagen en formato .pdf
    plt.show()


if __name__ == '__main__':
    main()
