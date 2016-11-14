---
title: "使用實作 IDisposable 的物件"
description: "使用實作 IDisposable 的物件"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: df780a6e-734e-44b8-9747-9f7783f79e20
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 51655742b8975c84eae3f58c4ef0f7381a0bed6b

---

# <a name="using-objects-that-implement-idisposable"></a>使用實作 IDisposable 的物件

通用語言執行平台的記憶體回收行程會回收 Unmanaged 物件所使用的記憶體，但是使用 Unmanaged 資源的類型會實作 [IDisposable](xref:System.IDisposable) 介面會允許回收這個 Unmanaged 記憶體。 實作 [IDisposable](xref:System.IDisposable) 的物件使用完畢時，您應呼叫物件的 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作。 您可以使用下列其中一種做法：

* 使用 C# `using` 陳述式或 Visual Basic `Using` 陳述式。

* 藉由實作 `try/finally` 區塊。 

## <a name="the-using-statement"></a>using 陳述式

C# 中的 `using` 陳述式和 Visual Basic 中的 `Using` 陳述式可簡化建立和清除物件所必須撰寫的程式碼。 `using` 陳述式會取得一項或多項資源、執行您指定的陳述式，然後自動處置該物件。 不過，`using` 陳述式只對建構物件的方法範圍內所使用的物件有其實用之處。 

下列範例會使用 `using` 陳述式建立和發行 [System.IO.StreamReader](xref:System.IO.StreamReader) 物件。

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      using (StreamReader s = new StreamReader("File1.txt")) {
         int charsRead = 0;
         while (s.Peek() != -1) {
            charsRead = s.Read(buffer, 0, buffer.Length);
            //
            // Process characters read.
            //   
         }
         s.Close();    
      }

   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
      Using s As New StreamReader("File1.txt")
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      End Using
   End Sub
End Module
```

請注意，雖然 [StreamReader](xref:System.IO.StreamReader) 類別會實作 [IDisposable](xref:System.IDisposable) 介面，指出它使用的是 Unmanaged 資源，但是這個範例並不會明確呼叫 [StreamReader.Dispose](xref:System.IO.StreamReader.Dispose(System.Boolean)) 方法。 當 C# 或 Visual Basic 編譯器遇到 `using` 陳述式時，會發出相當於下列明確包含 `try/finally` 區塊之程式碼的中繼語言 (IL)。 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      {
         StreamReader s = new StreamReader("File1.txt"); 
         try {
            int charsRead = 0;
            while (s.Peek() != -1) {
               charsRead = s.Read(buffer, 0, buffer.Length);
               //
               // Process characters read.
               //   
            }
            s.Close();
         }
         finally {
            if (s != null)
               ((IDisposable)s).Dispose();     
         }       
      }
   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
''      Dim s As New StreamReader("File1.txt")
With s As New StreamReader("File1.txt")
      Try
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      Finally
         If s IsNot Nothing Then DirectCast(s, IDisposable).Dispose()
      End Try
End With
   End Sub
End Module
```

C# `using` 陳述式還可讓您以單一陳述式取得多項資源，其內部相當於巢狀的 using 陳述式。 下列範例會具現化兩個 [StreamReader](xref:System.IO.StreamReader) 物件，以便讀取兩個不同檔案的內容。 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer1 = new Char[50], buffer2 = new Char[50];

      using (StreamReader version1 = new StreamReader("file1.txt"),
                          version2 = new StreamReader("file2.txt")) {
         int charsRead1, charsRead2 = 0;
         while (version1.Peek() != -1 && version2.Peek() != -1) {
            charsRead1 = version1.Read(buffer1, 0, buffer1.Length);
            charsRead2 = version2.Read(buffer2, 0, buffer2.Length);
            //
            // Process characters read.
            //
         }
         version1.Close();
         version2.Close();
      }
   }
}
```

## <a name="tryfinally-block"></a>Try/finally 區塊

您可以選擇直接實作 `try/finally` 區塊，而不將 `try/finally` 區塊包裝在 `using` 陳述式中。 這可成為您的個人編碼風格，也可能基於下列其中一個原因而這樣做： 

* 包含 `catch` 區塊以處理 `try` 區塊中擲回的任何例外狀況。 否則，當 `try/catch` 區塊不存在時，`using` 陳述式擲回的所有例外狀況都會是未處理，就連 `using` 區塊中擲回的任何例外狀況也一樣。 

* 若要將實作 [IDisposable](xref:System.IDisposable) 且範圍對於物件宣告所在區塊並非區域的物件具現化。 

下列範例類似上述範例，不過它會使用 `try/catch/finally` 區塊具現化、使用和處置 [StreamReader](xref:System.IO.StreamReader) 物件，以及處理 [StreamReader](xref:System.IO.StreamReader) 建構函式和其 [ReadToEnd](xref:System.IO.StreamReader.ReadToEnd) 方法擲回的所有例外狀況。 請注意，在 `finally` 中的程式碼會先確認實作 [IDisposable](xref:System.IDisposable) 的物件不是 `null`，再呼叫 [Dispose](xref:System.IDisposable.Dispose) 方法。 若未這樣做，可能導致執行階段產生 [NullReferenceException](xref:System.NullReferenceException) 例外狀況。 

```cs
using System;
using System.Globalization;
using System.IO;

public class Example
{
   public static void Main()
   {
      StreamReader sr = null;
      try {
         sr = new StreamReader("file1.txt");
         String contents = sr.ReadToEnd();
         sr.Close();
         Console.WriteLine("The file has {0} text elements.", 
                           new StringInfo(contents).LengthInTextElements);    
      }      
      catch (FileNotFoundException) {
         Console.WriteLine("The file cannot be found.");
      }   
      catch (IOException) {
         Console.WriteLine("An I/O error has occurred.");
      }
      catch (OutOfMemoryException) {
         Console.WriteLine("There is insufficient memory to read the file.");   
      }
      finally {
         if (sr != null) sr.Dispose();     
      }
   }
}
```

```vb
Imports System.Globalization
Imports System.IO

Module Example
   Public Sub Main()
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader("file1.txt")
         Dim contents As String = sr.ReadToEnd()
         sr.Close()
         Console.WriteLine("The file has {0} text elements.", 
                           New StringInfo(contents).LengthInTextElements)    
      Catch e As FileNotFoundException
         Console.WriteLine("The file cannot be found.")
      Catch e As IOException
         Console.WriteLine("An I/O error has occurred.")
      Catch e As OutOfMemoryException
         Console.WriteLine("There is insufficient memory to read the file.")   
      Finally 
         If sr IsNot Nothing Then sr.Dispose()     
      End Try
   End Sub
End Module
```

如果您因為程式語言不支援 `using` 陳述式，但是允許直接呼叫 [Dispose](xref:System.IDisposable.Dispose) 方法，而選擇實作或必須實作 `try/finally` 區塊，您可以遵循這個基本模式。 

## <a name="see-also"></a>另請參閱

[清除 Unmanaged 資源](unmanaged.md)





<!--HONumber=Nov16_HO1-->


