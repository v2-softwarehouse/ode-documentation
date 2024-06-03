# ODE GUI
Listening to UseCase<P, R> that have been processed and sent from of the Business layer. Waiting for outputs on appropriate channels.

## GUI Bases
Through pre-defined support base classes **BaseController** and **BaseViewModel**, capable of listening and dispatching the use cases processed to the corresponding view.

- **BaseController:** can dispatch and process use case options.
- **BaseViewModel:** must dispatch the use case options.


## Features on GUI Bases
- **Dispatch or Process ODE UseCase**: Dispatch a UseCase<P, R>.
- **Dispatch or Process Chain ODE UseCase**: Dispatch a UseCase<P, R> that depends on other use cases.
- **Dispatch or Process Sequence ODE UseCase**: Dispatch a list of UseCase<P, R> that are independent of each other.

### Dispatch or Process ODE UseCase
````{tab} Python
  ```python
class PresenterImpl(GatewayInjector, BaseController, Presenter):
    ...

    def get_house(self, page :int):
        self.dispatch_use_case(page, self.fetcher_api)
  ```
  ````
  ````{tab} Swift
  ```swift
class UseCaseViewModel: BaseViewModel, 
    UseCaseController {
    ...

    func doFetch(channelName: String) {
        dispatchUseCase(param: "bulbasaur", useCase: getUseCase) { output in
            self.postValue(channelName: channelName, value: output)
      }
    }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class UseCaseViewModel : BaseViewModel(), 
    UseCaseController {
    ...

    override fun doFetch(channelName: String) {
        dispatchUseCase("bulbasaur", getUseCase) { postValue(channelName, it) }
    }
}
  ```
  ````
  ````{tab} C#
  ```csharp
class UnitPresenterImpl : BaseController, UnitPresenter
{
    ...

    public UnitPokemon doFetch()
    {
        return processUseCase("bulbasaur", get)?.value;
    }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
//TODO
  ```
  ````

### Dispatch or Process Chain ODE UseCase
````{tab} Python
  ```python
class PresenterImpl(GatewayInjector, BaseController, Presenter):
    ...
            
    def get_house(self, page :int):
        chained = ChainedUseCase(getBulbasaur, getVenusaur)
        self.dispatch_use_case(page, self.chained)
  ```
  ````
  ````{tab} Swift
  ```swift
class ChainUseCaseViewModel: BaseViewModel, ChainUseCaseController {
  ...

  func doFetch(channelName: String) {
      let chained = ChainedUseCase(first: getBulbasaur, second: getIvysaur)
      dispatchUseCase(param: nil, useCase: chained){ output in
          self.postValue(channelName: channelName, value: output)
    }
  }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
class ChainUseCaseViewModel : BaseViewModel(), ChainUseCaseController {
  ...

  override fun doFetch(channelName: String) {
      val chained = ChainedUseCase(getBulbasaur, getVenusaur)
      dispatchUseCase(null, chained) { postValue(channelName, it) }
  }
}
  ```
  ````
  ````{tab} C#
  ```csharp
class UnitPresenterImpl : BaseController, UnitPresenter
{
    ...

    public List<UnitPokemon> doFetch()
    {
        var chainedUseCase = new ChainedUseCase(getBulbasaur, getIvysaur);
        return processUseCase(null, chainedUseCase).value;
    }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
//TODO
  ```
  ````

### Dispatch or Process Sequence ODE UseCase
````{tab} Python
  ```python
class PresenterImpl(GatewayInjector, BaseController, Presenter):
    ...
            
    def get_house(self, page :int):
        sequence = SequenceUseCase.builder()
            .add(getBulbasaur)
            .add(getIvysaur)
            .add(getVenusaur)
            .build()
        self.dispatch_use_case(None, sequence)
  ```
  ````
  ````{tab} Swift
  ```swift
class SequenceUseCaseViewModel: BaseViewModel, 
    SequenceUseCaseController {
    ...

    func doFetch(channelName: String) {
        let sequence = SequenceUseCase
            .Builder()
            .add(useCase: getBulbasaur)
            .add(useCase: getIvysaur)
            .add(useCase: getVenusaur)
            .build()
        dispatchUseCase(param: nil, useCase: sequence){ output in
            self.postValue(channelName: channelName, value: output)
      }
    }
}
  ```
  ````
  ````{tab} Kotlin
  ```kotlin
SequenceUseCaseViewModel : BaseViewModel(), 
    SequenceUseCaseController {
    ...

    override fun doFetch(channelName: String) {
        val sequence = SequenceUseCase.builder()
            .add(getBulbasaur)
            .add(getIvysaur)
            .add(getVenusaur)
            .build()
        dispatchUseCase(null, sequence) {
            postValue(channelName, it)
        }
    }
}
  ```
  ````
  ````{tab} C#
  ```csharp
class SequencePresenterImpl : BaseController, SequencePresenter
{
    ...
    
    public List<SequencePokemon> doFetch()
    {
        var sequence = SequenceUseCase.Builder()
        .add(getBulbasaur)
        .add(getIvysaur)
        .add(getVenusaur)
        .build();
        return processUseCase(null, sequence)?.value;
    }
}
  ```
  ````
  ````{tab} TypeScript
  ```javascript
//TODO
  ```
  ````