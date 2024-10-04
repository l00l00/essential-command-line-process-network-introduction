The command `ps -ef>ps-ef.sh | nvim` is problematic because of how pipes (`|`) work and how redirection (`>`) is handled in the shell.

### Breakdown of the command:
1. `ps -ef`: This lists all running processes in a detailed format.
2. `>ps-ef.sh`: This redirects the output of `ps -ef` to the file `ps-ef.sh`.
3. `| nvim`: This tries to send the output of the previous command to `nvim` (through the pipe).

### Why it doesn't work:
- **Redirection (`>`)** takes precedence over the pipe (`|`). So, the output of `ps -ef` is redirected to the file `ps-ef.sh`, but there's **no output left to send to `nvim`** via the pipe.
- Since the output has already been redirected to a file, nothing is passed to the pipe (`|`), so `nvim` opens without content to edit.

### Correct approach:
To achieve both the file redirection and opening the content in `nvim`, you can either:
1. **Redirect and open the file in `nvim` separately**:
   ```bash
   ps -ef > ps-ef.sh && nvim ps-ef.sh
   ```
   This first saves the output to the file `ps-ef.sh` and then opens it in `nvim`.

2. **Use `tee` to split the output**:
   ```bash
   ps -ef | tee ps-ef.sh | nvim -
   ```
   The `tee` command sends the output both to the file (`ps-ef.sh`) and to the standard output, which is then piped into `nvim`. The `nvim -` command opens the standard input as a new buffer in `nvim`.

Both of these methods will work and handle the output as expected!
