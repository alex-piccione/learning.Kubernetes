# Example 2


## Build & Run
``docker build -t kuard .``
``docker run --rm -p 8080:8080 kuard``

## Tag & Push

Once you are logged in your Docker repository
``docker tag kuard gcr.io/kuar-demo/kuard-amd64:blue``
``docker push kuard gcr.io/kuar-demo/kuard-amd64:blue``