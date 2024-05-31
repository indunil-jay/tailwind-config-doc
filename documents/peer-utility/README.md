```javascript
const App = () => {
  return (
    <div className="min-h-screen px-8 py-16">
      <div className="flex flex-col relative">
        <input
          id="email"
          name="email"
          type="text"
          placeholder="Email Address"
          className="h-10 w-full border-b-2 border-gray-300 text-gray-900 
          focus:outline-none focus:border-rose-600
          placeholder-transparent
          peer
          "
        />
        <label
          htmlFor="email"
          className="absolute left-0 -top-3.5 text-gray-600 text-sm transition-all
           peer-placeholder-shown:text-base
           peer-placeholder-shown:text-gray-400
           peer-placeholder-shown:top-2
           peer-focus:-top-3.5
           peer-focus:text-gray-600
           peer-focus:text-sm
          "
        >
          Email Address
        </label>
      </div>
    </div>
  );
};

export default App;
```
