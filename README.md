# Who is `tarsil`?

`tarsil` is also known as Tiago Silva, not the football player but a Software Engineer.

Passionate to his core, `tarsil` is also the creator of [Esmerald][esmerald], [Lilya][lilya],
[Edgy][edgy], [Mongoz][mongoz], [Asyncz][asyncz] and many open source tools out there.

## Hello from `tarsil`

Nothing like using [Esmerald][esmerald] to say hi.

```shell
$ pip install esmerald
$ pip install uvicorn
```

Then, inside an `app.py`, add this.

```python
import uvicorn

from esmerald import Esmerald, Gateway, JSONResponse, Request, get


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


app = Esmerald(
    routes=[
        Gateway("/esmerald", handler=welcome),
        Gateway("/esmerald/{user}", handler=user),
        Gateway("/esmerald/in-request/{user}", handler=user_in_request),
    ]
)


if __name__ == "__main__":
    uvicorn.run(app, port=8000)
```

In the end, run the `./app.py` and access your localhost in the endpoints. Have fun!

[esmerald]: https://esmerald.dev
[lilya]: https://lilya.dev
[edgy]: https://edgy.dymmond.com
[mongoz]: https://mongoz.dymmond.com
[asyncz]: https://asyncz.dymmond.com
