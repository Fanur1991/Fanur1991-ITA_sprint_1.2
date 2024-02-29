# Patrón de Diseño Estrategia en mi Proyecto ToDo List

Quiero compartir cómo podría implementar el patrón de diseño **Estrategia** en mi proyecto de lista de tareas (ToDo List) desarrollado en TypeScript. Aunque actualmente no he aplicado este patrón en mi proyecto, creo que sería una excelente adición para mejorar la flexibilidad y extensibilidad del código.

## ¿Qué es el Patrón Estrategia?

El patrón **Estrategia** es un patrón de diseño que nos permite cambiar el algoritmo utilizado en una operación en tiempo de ejecución. Esto significa que podemos intercambiar diferentes algoritmos que realizan una tarea específica según nuestras necesidades.

## ¿Cómo Funcionaría en mi Proyecto?

En mi aplicación ToDo List, este patrón me permitiría manejar diferentes formas de filtrar y ordenar las tareas. Por ejemplo, podría tener estrategias para filtrar solo las tareas completadas, solo las pendientes, o para ordenar las tareas por fecha o por nombre.

### Interfaz de Estrategia

Primero, definiría una interfaz ITodoStrategy que describiría las operaciones de filtrado y ordenación:
```typescript
interface IToDoStrategy {
  filter(todos: ToDo[]): ToDo[];
  sort(todos: ToDo[]): ToDo[];
}

### Estrategias Concretas

<p>Luego, implementaría diferentes estrategias que cumplen con esta interfaz. Por ejemplo, una estrategia por defecto que no filtra las tareas y las ordena por su estado de completado:</p>
<p>class DefaultToDoStrategy implements IToDoStrategy {
  filter(todos: ToDo[]): ToDo[] {
    return todos;
  }

  sort(todos: ToDo[]): ToDo[] {
    return todos.sort((a, b) => Number(a.isCompleted) - Number(b.isCompleted));
  }
}
</p>

<h5>Integración en ToDoList</h5>
<p>Integraría estas estrategias en mi clase ToDoList, permitiéndome cambiar cómo se muestran las tareas en tiempo de ejecución:</p>
<p>export class ToDoList {
  private strategy: IToDoStrategy;

  constructor(strategy: IToDoStrategy = new DefaultToDoStrategy()) {
    this.strategy = strategy;
  }

  getToDos(): IToDo[] {
    let filteredAndSorted = this.strategy.sort(this.strategy.filter(this.toDoList));
    return filteredAndSorted;
  }

  setStrategy(strategy: IToDoStrategy) {
    this.strategy = strategy;
  }
}
</p>

<h3>Beneficios de Aplicar el Patrón Estrategia</h3>

<ul>
  <li>Flexibilidad: Me permite cambiar la forma en que se muestran las tareas sin necesidad de modificar el código principal de la lista de tareas.</li>
  <li>Extensibilidad: Facilita la adición de nuevas formas de filtrar y ordenar las tareas sin afectar otras partes del código.</li>
</ul>

<h3>Conclusión</h3>

<p>Aunque aún no he implementado este patrón en mi proyecto, veo un gran potencial en su aplicación para hacer mi código más modular, flexible y fácil de expandir en el futuro. Sería una excelente manera de preparar mi proyecto para futuras mejoras y funcionalidades.</p>




















