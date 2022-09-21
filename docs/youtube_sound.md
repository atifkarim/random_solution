No sound in Youtube
===================

Sometimes sound does not work in Youtube. This is caused by YouTube Rendering problem

- **Warning** error message `Audio Rendering Erro, Please restart your Computer`

- **Solution** open a terminal and run
    ```sh
    pulseaudio -k && sudo alsa force-reload
    ```