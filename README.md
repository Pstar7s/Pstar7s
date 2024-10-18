let mode = 'normal';

document.addEventListener('keydown', (event) => {
    const editor = document.getElementById('editor');
    const statusBar = document.getElementById('status-bar');

    if (mode === 'normal') {
        if (event.key === 'i') {
            mode = 'insert';
            statusBar.textContent = '-- INSERT --';
            editor.contentEditable = true;
        } else if (event.key === ':') {
            const command = prompt('Enter command (e.g., :w, :q):');
            if (command === ':q') {
                alert('Quitting Vim-like editor');
                window.close();
            } else if (command === ':w') {
                alert('File saved (simulated)');
            }
        }
    } else if (mode === 'insert') {
        if (event.key === 'Escape') {
            mode = 'normal';
            statusBar.textContent = '-- NORMAL --';
            editor.contentEditable = false;
        }
    }
});
