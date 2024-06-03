# ODE UseCase
Abstracting, simplifying and standardizing works when invoking, saving and dispatching UseCase<P, R> to the View Layer.

## Features
- **Process UseCase**: Starts the process of Guard, Dispatch and Handle result of UseCase<P, R>.
- **Guard of UseCase**: Safely blocks the execution of a UseCase<P, R> and prevents cyclomatic complexity in the presenter.

### ODE UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def guard(self, param: int = None) -> bool:
        return param is not None
        
    ...
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase<String, Any> {
    var repo: UseCaseRepository
    
    init(repo: UseCaseRepository) {
        self.repo = repo
    }
    
    override func onGuard(param: String?) -> Bool {
        return param != nil
    }
    ...
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(
      private val repo: UseCaseRepository
  ) : UseCase<String, Any>() {

      override fun guard(param: String?): Boolean {
          return param != null
      }
      ...
}
  ```
  ````
  ````{tab} C#
  ```csharp
public class UnitGET : UseCase<string, Any>
{
    UnitRepository repo { get; set; }

    public UnitGET(UnitRepository repo) : base() {
        this.repo = repo;
    }

    public override bool guard(string param)
    {
        return param != null
    }
   ...
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase<string, any> {
    private repo: Repository;
    
    guard(param: string | null): boolean {
        return param != null
    }
}
  ```
  ````

### Guard of ODE UseCase
````{tab} Python
  ```python
class GETAPIUseCase(UseCase[int, Any]):
    def __init__(self, repo: UseCaseRepository):
        self.repo = repo

    def guard(self, param: int = None) -> bool:
        return param is not None
        
    ...
  ```
  ````
  ````{tab} Swift
  ```swift
class GETUseCase : UseCase<String, Any> {
    var repo: UseCaseRepository
    
    init(repo: UseCaseRepository) {
        self.repo = repo
    }
    
    override func onGuard(param: String?) -> Bool {
        return param != nil
    }
    ...
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(
      private val repo: UseCaseRepository
  ) : UseCase<String, Any>() {

      override fun guard(param: String?): Boolean {
          return param != null
      }
      ...
}
  ```
  ````
  ````{tab} C#
  ```csharp
public class UnitGET : UseCase<string, Any>
{
    UnitRepository repo { get; set; }

    public UnitGET(UnitRepository repo) : base() {
        this.repo = repo;
    }

    public override bool guard(string param)
    {
        return param != null
    }
   ...
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
class GETUseCase extends UseCase<string, any> {
    private repo: Repository;
    
    guard(param: string | null): boolean {
        return param != null
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
        ...
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
    ...
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class GETUseCase(private val repo: UseCaseRepository) 
: UseCase() {

  override fun execute(param: String?): Output {
      ...
  }
}
  ```
  ````
  ````{tab} C#
  ```csharp
public class GETUseCase : UseCase
{
  UseCaseRepository repo { get; set; }

  public UnitGET(UseCaseRepository repo) : base() {
      this.repo = repo;
  }

  public override Output execute(string param)
  {
      ...
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
        ...
    }
}
  ```
  ````