## Blazor Component 폐기(Dispose)

참고: [Component Disposal in Blazor](https://codemurals.blogspot.com/2021/12/component-disposal-in-blazor.html)

개발자는 애플리케이션에서 사용되는 리소스를 관리해야 합니다. 메모리 누수를 방지하는 데 도움이 되는 관리되지 않는 리소스를 해제해야 합니다. Blazor는 구성 요소를 릴리스하기 위한 두 가지 구현을 제공합니다. IDisposable 및 IAsyncDisposable


IDisposable
```c#
@page "/sample"

@implements IDisposable

@code {
    Movie movieObj;

    private void CollectValues()
    {
        movieObj = new Movie();
	...
	...
	...
    }

    public void Dispose()
    {
        movieObj?.Dispose();
    }
}
```


IAsyncDisposable
```c#
@page "/sample"

@implements IAsyncDisposable

@code {
    Movie movieObj;
    string str;

    private void  CollectValues()
    {
        movieObj = new Movie();
	...
	...
	...
    }

    public async ValueTask DisposeAsync()
    {
        if (movieObj != null)
        {
            await movieObj.DisposeAsync();
        }
    }
}
```