// Clase abstracta Producto
abstract class Producto {
    protected String nombre;
    protected double precio;

    public Producto(String nombre, double precio) {
        this.nombre = nombre;
        this.precio = precio;
    }

    public abstract void mostrarDetalles();
    public double obtenerPrecio() {
        return precio;
    }
}

// Interfaz Inventariable
interface Inventariable {
    void agregarStock(int cantidad);
    void reducirStock(int cantidad);
}

// Clase ProductoElectronico
class ProductoElectronico extends Producto implements Inventariable {
    private int stock;

    public ProductoElectronico(String nombre, double precio) {
        super(nombre, precio);
        this.stock = 0;
    }

    @Override
    public void mostrarDetalles() {
        System.out.println("Producto Electrónico: " + nombre + ", Precio: " + precio + ", Stock: " + stock);
    }

    @Override
    public void agregarStock(int cantidad) {
        stock += cantidad;
    }

    @Override
    public void reducirStock(int cantidad) {
        stock -= cantidad;
    }
}

// Clase ProductoAlimenticio
class ProductoAlimenticio extends Producto implements Inventariable {
    private int stock;

    public ProductoAlimenticio(String nombre, double precio) {
        super(nombre, precio);
        this.stock = 0;
    }

    @Override
    public void mostrarDetalles() {
        System.out.println("Producto Alimenticio: " + nombre + ", Precio: " + precio + ", Stock: " + stock);
    }

    @Override
    public void agregarStock(int cantidad) {
        stock += cantidad;
    }

    @Override
    public void reducirStock(int cantidad) {
        stock -= cantidad;
    }
}

// Clase principal GestionInventario
public class GestionInventario {
    public static void main(String[] args) {
        Producto producto1 = new ProductoElectronico("Laptop", 1500.00);
        Producto producto2 = new ProductoAlimenticio("Manzana", 0.50);

        // Agregar stock
        ((Inventariable) producto1).agregarStock(10);
        ((Inventariable) producto2).agregarStock(50);

        // Mostrar detalles
        producto1.mostrarDetalles();
        producto2.mostrarDetalles();
    }
}
