# Ink-ABI

## letlang pseudocode
```
type Animal = trait {
  fun Speak(let Env: Environment): Unit
}

type Petable = trait {
  fun Pet(let Env: Environment): Unit
}

type Pet = trait {
  extends Animal
  extends Petable
}

type Cat = primitive {
  extends Pet
  
  override fun Speak(let Env: Environment): Unit {
    Env.WriteLine("Meow")
  }
  
  override fun Pet(let Env: Environment): Unit {
    Env.WriteLine("Purr")
  }
}
```

## c pseudocode

```
// Definition of interface Animal

struct Animal__imt {
  void *class;
  void (*speak)(Animal__ref this, Environment__ref env);
}

struct Animal__ref {
  Animal__imt *imt;
  void *data;
}


// Definition of interface Petable

struct Petable__imt {
  void *class;
  void (*pet)(Pettable__ref this, Environment__ref env);
}

struct Petable__ref {
  Petable__imt *imt;
  void *data;
}


// Definition of interface Pet

struct Pet__imt {
  void *class;
  void (*speak)(Pet__ref this, Environment__ref env);
  void (*pet)(Pet__ref this, Environment__ref env);
}

struct Pet__ref {
  Pet__imt *imt;
  void *data;
}


// Definition of Cat

struct Cat__data {}
char[] Cat__class = {};


// Definitions of Cat's IMTs

struct Animal__imt Cat_as_Animal_imt = {
  .class = (void*) &Cat__class;
  .speak = &Cat_as_Animal__speak;
}

struct Petable__imt Cat_as_Petable_imt = {
  .class = (void*) &Cat__class;
  .pet = &Cat_as_Petable__pet;
}

struct Pet__imt Cat_as_Pet_imt = {
  .class = (void*) &Cat__class;
  .speak = &Cat_as_Pet__speak;
  .pet = &Cat_as_Pet__pet;
}


// Definition of Cat's adapter methods

void Cat_as_Animal__speak(Animal__ref this, Environment__ref env) {
  if (this.imt->class != &Cat__class) {
    classCastException();
  }
  else {
    Cat__speak(this.data, env);
  }
}

void Cat_as_Petable__pet(Petable__ref this, Environment__ref env) {
  if (this.imt->class != &Cat__class) {
    classCastException();
  }
  else {
    Cat__pet(env);
  }
}

void Cat_as_Pet__speak(Pet__ref this, Environment__ref env) {
  if (this.imt->class != &Cat__class) {
    classCastException();
  }
  else {
    Cat__speak(env);
  }
}

void Cat_as_Pet__pet(Pet__ref this, Environment__ref env) {
  if (this.imt->class != &Cat__class) {
    classCastException();
  }
  else {
    Cat__pet(env);
  }
}


// Definitions of Cat's method implementations

void Cat__speak(Environment__ref env) {
  env.imt->writeLine(env, "Meow");
}

void Cat__pet(Environment__ref env) {
  env.imt->writeLine(env, "Purr");
}
```


