# Who is `tarsil`?

`tarsil` is also known as Tiago Silva, not the football player but a Software Engineer.

Passionate to his core, `tarsil` is also the creator of [Ravyn][ravyn], [Lilya][lilya],
[Edgy][edgy], [AsyncMQ][asyncmq], [Mongoz][mongoz], [Asyncz][asyncz] and many open source tools out there.

I do have a [discord channel](https://discord.gg/tmE8WEW8az) if you want to ask me anything about what I do and my tools.

## Hello from `tarsil`

Nothing like using [Ravyn][ravyn] to say hi.

```shell
$ pip install ravyn
$ pip install uvicorn
```

Then, inside an `app.py`, add this.

```python
import uvicorn

from ravyn import Ravyn, Gateway, JSONResponse, Request, get


@get()
def welcome() -> JSONResponse:
    return JSONResponse({"message": "Welcome to tarsil's Github"})


@get()
def user(user: str) -> JSONResponse:
    return JSONResponse({"message": f"Welcome to tarsil's Github, {user}"})


@get()
def user_in_request(request: Request) -> JSONResponse:
    user = request.path_params["user"]
    return JSONResponse({"message": f"Welcome to tarsil's Github, {user}"})


app = Ravyn(
    routes=[
        Gateway("/ravyn", handler=welcome),
        Gateway("/ravyn/{user}", handler=user),
        Gateway("/ravyn/in-request/{user}", handler=user_in_request),
    ]
)


if __name__ == "__main__":
    uvicorn.run(app, port=8000)
```

In the end, run the `./app.py` and access your localhost in the endpoints. Have fun!

[ravyn]: https://ravyn.dev
[lilya]: https://lilya.dev
[edgy]: https://edgy.dymmond.com
[mongoz]: https://mongoz.dymmond.com
[asyncz]: https://asyncz.dymmond.com
[sayer]: https://sayer.dymmond.com
[asyncmq]: https://asyncmq.dymmond.com
