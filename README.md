# napiwrapper

Start of a wrapper for [napi](https://github.com/nodejs/node-addon-api)
---------------------------------------------------------------------

*Wrapping the wrapper now are we?*

-   **I guess so.**

*How can you test this, it's just one file?*

-   **[Look here](https://github.com/wheresjames/libblank), build the npm module.**

*There's lots missing.*

-   **I'm just going to add it as needed.**

*What does it do anyway?*

-   **Thought you'd never ask...**

&nbsp;

---------------------------------------------------------------------
## Example: Exporting a function

```c++
    std::string sayHello(const std::string &name)
    {
        return std::string("Hello, ") + name;
    }

    NAPI_BEGIN_EXPORTS(MyModule)
        NAPI_EXPORT_FUNCTION(sayHello)
    NAPI_END_EXPORTS()
```

&nbsp;

---------------------------------------------------------------------
## Example: Exporting a class


```c++
    class CTestClass
    {
    public:
        CTestClass() : m_x(0) {};
        CTestClass(int x) : m_x(x) {};
        void setX(int x) { m_x = x; }
        int getX() { return m_x; }
    private:
        int m_x;
    };

    NAPI_DEFINE_CLASS(CTestClass)
        NAPI_CONSTRUCTOR_1(CTestClass)
        NAPI_END_CONSTRUCTORS(CTestClass)
        NAPI_MEMBER_FUNCTION(CTestClass, setX)
        NAPI_MEMBER_FUNCTION(CTestClass, getX)
    NAPI_DEFINE_CLASS_END()

    NAPI_BEGIN_EXPORTS(MyModule)
        NAPI_EXPORT_CLASS(CTestClass)
    NAPI_END_EXPORTS()
```
