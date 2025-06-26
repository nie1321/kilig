function debounce(func, threshold, callImmediately) {
  let timeout;

  return function (...args) {
    const context = this;

    const delayed = function () {
      timeout = null;
      if (!callImmediately) {
        func.apply(context, args);
      }
    };

    const callNow = callImmediately && !timeout;

    clearTimeout(timeout);
    timeout = setTimeout(delayed, threshold);

    if (callNow) {
      func.apply(context, args);
    }
  };
}
