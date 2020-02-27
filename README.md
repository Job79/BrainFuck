# BrainFuck
Small Brainfuck interpreter written in c#

```cs
static void Run(char[] c)
{
    var s = new List<byte>{0};
    int p = 0, bc = 0;

    for (int i = 0; i < c.Length; i++)
    {
        if (c[i] == '>' && s.Count == ++p) s.Add(0);
        else if (c[i] == '<') p--;
        else if (c[i] == '+') s[p]++;
        else if (c[i] == '-') s[p]--;
        else if (c[i] == '.') Console.Write((char)s[p]);
        else if (c[i] == ',') s[p] = (byte) Console.ReadKey().KeyChar;
        else if (c[i] == '[' && s[p] == 0 && bc++ != null)
            while (c[i] != ']' || bc != 0) bc += c[++i] == '[' ? 1 : c[i] == ']' ? -1 : 0;
        else if (c[i] == ']' && s[p] != 0 && bc++ != null)
            while (c[i] != '[' || bc != 0) bc += c[--i] == ']' ? 1 : c[i] == '[' ? -1 : 0;
    }
}
```
