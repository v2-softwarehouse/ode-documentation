# ODE Tasks
ODE concentrates a set of good development practices. Our role centers between the Business layer and the View layer.
Abstracting, simplifying and standardizing works when invoking, saving and dispatching UseCase<P, R> to the view layer.

## Features
- **Guard of UseCase**: Safely blocks the execution of a UseCase<P, R> and prevents cyclomatic complexity in the presenter.
- **Dispatch UseCase**: Dispatch a UseCase<P, R>.
- **Dispatch Chain UseCase**: Dispatch a UseCase<P, R> that depends on other use cases.
- **Dispatch Sequence UseCase**: Dispatch a list of UseCase<P, R> that are independent of each other.

### Guard of UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def execute(self, param: int) -> Output[Any]:
        fetch = self.repo.do_fetch(page=param)
        return ValueOutput(fetch)
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase {
  var repo: UseCaseRepository

  init(repo: UseCaseRepository) {
      self.repo = repo
  }

  override func execute(param: String?) -> Output {
      let fetch = repo.doFetch(name: param)
      return ValueOutput(value: fetch)
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(private val repo: UseCaseRepository) 
: UseCase() {

  override fun execute(param: String?): Output {
      val fetch = repo.doFetch(param)
      return ValueOutput(fetch)
  }
}
  ```
  ````
  ````{tab} C#
  ```cshart
public class GETUseCase : UseCase
{
  UseCaseRepository repo { get; set; }

  public UnitGET(UseCaseRepository repo) : base() {
      this.repo = repo;
  }

  public override Output execute(string param)
  {
      var fetch = repo.doFetch();
      return new ValueOutput(fetch);
  }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase {
    private repo: UseCaseRepository;

    constructor(repo: UseCaseRepository) {
        super();
        this.repo = repo;
    }

    execute(param: string | null): Output {
        const fetch = this.repo.doFetch(param);
        return new ValueOutput(fetch);
    }
}
  ```
  ````

### Dispatch UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def execute(self, param: int) -> Output[Any]:
        fetch = self.repo.do_fetch(page=param)
        return ValueOutput(fetch)
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase {
  var repo: UseCaseRepository

  init(repo: UseCaseRepository) {
      self.repo = repo
  }

  override func execute(param: String?) -> Output {
      let fetch = repo.doFetch(name: param)
      return ValueOutput(value: fetch)
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(private val repo: UseCaseRepository) 
: UseCase() {

  override fun execute(param: String?): Output {
      val fetch = repo.doFetch(param)
      return ValueOutput(fetch)
  }
}
  ```
  ````
  ````{tab} C#
  ```cshart
public class GETUseCase : UseCase
{
  UseCaseRepository repo { get; set; }

  public UnitGET(UseCaseRepository repo) : base() {
      this.repo = repo;
  }

  public override Output execute(string param)
  {
      var fetch = repo.doFetch();
      return new ValueOutput(fetch);
  }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase {
    private repo: UseCaseRepository;

    constructor(repo: UseCaseRepository) {
        super();
        this.repo = repo;
    }

    execute(param: string | null): Output {
        const fetch = this.repo.doFetch(param);
        return new ValueOutput(fetch);
    }
}
  ```
  ````

### Dispatch Chain UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def execute(self, param: int) -> Output[Any]:
        fetch = self.repo.do_fetch(page=param)
        return ValueOutput(fetch)
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase {
  var repo: UseCaseRepository

  init(repo: UseCaseRepository) {
      self.repo = repo
  }

  override func execute(param: String?) -> Output {
      let fetch = repo.doFetch(name: param)
      return ValueOutput(value: fetch)
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(private val repo: UseCaseRepository) 
: UseCase() {

  override fun execute(param: String?): Output {
      val fetch = repo.doFetch(param)
      return ValueOutput(fetch)
  }
}
  ```
  ````
  ````{tab} C#
  ```cshart
public class GETUseCase : UseCase
{
  UseCaseRepository repo { get; set; }

  public UnitGET(UseCaseRepository repo) : base() {
      this.repo = repo;
  }

  public override Output execute(string param)
  {
      var fetch = repo.doFetch();
      return new ValueOutput(fetch);
  }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase {
    private repo: UseCaseRepository;

    constructor(repo: UseCaseRepository) {
        super();
        this.repo = repo;
    }

    execute(param: string | null): Output {
        const fetch = this.repo.doFetch(param);
        return new ValueOutput(fetch);
    }
}
  ```
  ````

### Dispatch Sequence UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def execute(self, param: int) -> Output[Any]:
        fetch = self.repo.do_fetch(page=param)
        return ValueOutput(fetch)
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase {
  var repo: UseCaseRepository

  init(repo: UseCaseRepository) {
      self.repo = repo
  }

  override func execute(param: String?) -> Output {
      let fetch = repo.doFetch(name: param)
      return ValueOutput(value: fetch)
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(private val repo: UseCaseRepository) 
: UseCase() {

  override fun execute(param: String?): Output {
      val fetch = repo.doFetch(param)
      return ValueOutput(fetch)
  }
}
  ```
  ````
  ````{tab} C#
  ```cshart
public class GETUseCase : UseCase
{
  UseCaseRepository repo { get; set; }

  public UnitGET(UseCaseRepository repo) : base() {
      this.repo = repo;
  }

  public override Output execute(string param)
  {
      var fetch = repo.doFetch();
      return new ValueOutput(fetch);
  }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase {
    private repo: UseCaseRepository;

    constructor(repo: UseCaseRepository) {
        super();
        this.repo = repo;
    }

    execute(param: string | null): Output {
        const fetch = this.repo.doFetch(param);
        return new ValueOutput(fetch);
    }
}
  ```
  ````