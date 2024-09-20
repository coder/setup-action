# Setup [Coder](https://github.com/coder/coder)

Downloads and Configures Coder.

## Usage

Create a GitHub secret named `CODER_SESSION_TOKEN` with your coder session token
You can generate a long lived session token by running the following command in
your browser console while logged into Coder with a **Template Admin** or
**Owner** role.

    ```shell
      coder token create --lifetime 8760h --name "GitHub Actions"
    ```

```yaml
jobs:
  setup-coder:
    runs-on: ubuntu-latest
    steps:
      - name: Setup Coder
        uses: coder/setup-action@v1
        with:
          access_url: 'https://dev.coder.com'
          coder_session_token: ${{ secrets.CODER_SESSION_TOKEN }}
```

## Inputs

| Name                      | Description                                                              | Default |
| ------------------------- | ------------------------------------------------------------------------ | ------- |
| **`access_url`**          | **Required** The url of coder deployment (e.g. <https://dev.coder.com>). | -       |
| **`coder_session_token`** | **Required** The session token of coder.                                 | -       |
