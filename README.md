# pokemongo-hash-sharp
Managed C# code for the Pokemon Go API request signature hash (port of "encrypt.c")


________

Project contains a fully managed port of the `encrypt.c` code as well as a p/invoke wrapper for the native encrypt.dll binaries. 

The managed lib is a PCL that targets .NET 4.5.1, ASP.NET Core, Xamarin.iOS/Android/Mac.


Both libs should work on about any mono platform. However, only the 32bit & 64bit encrypt.dll Windows binaries are included. 


________

### Sample usage

```csharp
byte[] input = System.Text.Encoding.UTF8.GetBytes("Sample input data..");
byte[] iv = new byte[32];
new Random().NextBytes(iv);

// using managed lib
byte[] output = PokemonGoHashSharp.Util.Hash(input, iv);

// using native wrapper lib
byte[] output = PokemonGoHashNative.Util.Hash(input, iv);

```


_______

#### Naming
I named the functions `Util.Hash(...)` rather than `Util.Encrypt(...)` because it looks a lot more like a hashing function than an encryption function. Feel free to correct me. 