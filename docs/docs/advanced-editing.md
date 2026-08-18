# Advanced Editing

1.  Clone [the code](https://github.com/ashleykleynhans/devops-docs).

    !!! tip
        Ensure you have uploaded your ssh pub key to [your GitHub
        profile](https://github.com/settings/keys) so you
        can easily clone over SSH.

    ```bash
    mkdir -p ~/src/work/devops-docs
    git clone git@github.com:ashleykleynhans/devops-docs.git ~/src/work/devops-docs
    cd ~/src/work/devops-docs
    ```

1.  Start the website by running `:::bash docker-compose up`.

    !!! important

        Every now and then, when the `requirements.txt` or docker
        files are updated you will need to run `docker-compose build`
        to update the docker image.

    ??? info "An alternative option using Python's virtualenv"

        [Alternative instructions](../quickstart-venv) are available
        to getting the website up locally and developing using
        Python's virtual environment if you prefer.

1.  Make your changes - edit the `.md` files - and view your changes
    in your web browser @ [http://127.0.0.1:8000/](http://127.0.0.1:8000/) .

    !!! attention

        Do take the time to setup your IDE to support the various markdown
        extensions. Or use one of the
        [presetup markdown editors out there](presetup markdown editors out there).

1.  Same as any code project, [submit a pull
    request](https://github.com/ashleykleynhans/devops-docs/pulls).
