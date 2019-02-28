# Some magic bugs in Java

## Class member variables are not initialized.
Yesterday I wrote a Class like this:
```
public class C{
	public int a;
	public int b;

	public C () {
		a = 0;
		b = 0;
	}

	public C (int a, int b) {
		a = a;
		b = b;
	}
}
```
When I used it today, I got nothing but 0 from anywhere. I initially thought that it is caused by the first constructor, so I removed it and tried again. Oh, it still worked as that. Then I realized that my second constructor is not working normally. Suddenly, I realized that it should not be written like this, where `a`s in the body are always the `a` which servers as the member variable.

I don't know why I wrote `a = a` and `b = b`. I don't know why I even strongly believed it would work. Well, maybe I wrote too much snippets like `foo(a=a, b=b, c=c)` and got confused.

Actually, when passing the parameters, you can write in that way. Because the first `a` is the name of the parameter and the second is the variable you are passing. While inside the body of a function, you couldn't do that because the compiler is not such intelligent. However, it is always your crappy code that causes the "bug".
