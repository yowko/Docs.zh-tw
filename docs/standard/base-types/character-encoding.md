---
title: ".NET 中的字元編碼"
description: ".NET 中的字元編碼"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 6080f5fa12a2391dd138828e0afc2219f1e3a11b

---

# <a name="character-encoding-in-net"></a>.NET 中的字元編碼

字元是可以用許多不同的方式來表示的抽象實體。 字元編碼是一套系統，可將所支援之字元集中的每個字元與代表該字元的特定值配對。 例如，摩斯密碼就是一種字元編碼，可將羅馬字母中的每個字元與適合透過電報線路傳輸的點和虛線圖樣配對。 電腦的字元編碼可將所支援之字元集中的每個字元與代表該字元的數值配對。 字元編碼包含兩個不同的元件：

* 編碼器，可將字元序列轉譯成數值 (位元組) 序列。

* 解碼器，可將位元組序列轉譯成字元序列。

字元編碼描述編碼器和解碼器運作時所依據的規則。 例如，[UTF8Encoding](xref:System.Text.UTF8Encoding) 類別描述編碼和解碼 8 位元 Unicode 轉換格式 (UTF-8) 的規則，該格式使用一到四個位元組來表示單一 Unicode 字元。 編碼和解碼也可包含驗證。 例如，[UnicodeEncoding](xref:System.Text.UnicodeEncoding) 類別會檢查所有 Surrogate，確定它們是由有效的 Surrogate 字組所組成。 (Surrogate 字組是由包含範圍從 U+D800 到 U+DBFF 之字碼指標的字元，後面接著包含範圍從 U+DC00 到 U+DFFF 之字碼指標的字元所組成)。後援策略決定編碼器如何處理無效的字元，或解碼器如何處理無效的位元組。 

> [!WARNING]
> .NET 編碼類別提供儲存和轉換字元資料的方法。 這些類別不應用來儲存字串格式的二進位資料。 根據使用的編碼方式，使用編碼類別將二進位資料轉換成字串格式可能會導致未預期的行為，並且產生不正確或損毀的資料。 若要將二進位資料轉換成字串格式，請使用 [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) 方法。 
 
.NET 使用 UTF-16 編碼 (以 [UnicodeEncoding](xref:System.Text.UnicodeEncoding) 類別表示) 來表示字元和字串。 以 Common Language Runtime 為目標的應用程式使用編碼器將 Common Language Runtime 所支援的 Unicode 字元表示對應至其他編碼配置， 並使用解碼器將非 Unicode 編碼的字元對應至 Unicode。

本主題包含下列章節：

* [.NET 中的編碼](#encodings-in-net)

* [選取編碼類別](#selecting-an-encoding-class)

* [使用編碼物件](#using-an-encoding-object)

* [選擇後援策略](#choosing-a-fallback-strategy)

* [實作自訂後援策略](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a>.NET 中的編碼

.NET 中的所有字元編碼類別都會繼承自 [System.Text.Encoding](xref:System.Text.Encoding) 類別，這是定義所有字元編碼共通功能的抽象類別。 若要存取 .NET 中實作的個別編碼物件，請執行下列作業：

* 使用 [Encoding](xref:System.Text.Encoding) 類別的靜態屬性，這些屬性會傳回代表 .NET 中可用之標準字元編碼 (ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32) 的物件。 例如，[Encoding.Unicode](xref:System.Text.Encoding.Unicode) 屬性會傳回 [UnicodeEncoding](xref:System.Text.UnicodeEncoding) 物件。 每個物件會使用取代後援，來處理無法編碼的字串和無法解碼的位元組  (如需詳細資訊，請參閱[取代後援](#replacement-fallback)一節)。

* 呼叫編碼的類別建構函式。 ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32 編碼的物件可以透過這種方式執行個體化。 每個物件預設會使用取代後援，來處理無法編碼的字串和無法解碼的位元組，不過您可以指定改為擲回例外狀況  (如需詳細資訊，請參閱[取代後援](#replacement-fallback)及[例外狀況後援](#exception-fallback)兩節)。

* 呼叫 [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) 建構函式，並將代表編碼的整數傳遞給該建構函式。 標準編碼物件使用取代後援，來處理無法編碼的字串和無法解碼的位元組，而字碼頁和雙位元組字元集 (DBCS) 編碼物件則是使用自動調整後援  (如需詳細資訊，請參閱[自動調整後援](#best-fit-fallback)一節)。

* 呼叫 [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) 方法，這個方法會傳回 .NET 中可用的任何標準、字碼頁或 DBCS 編碼。 多載可讓您同時為編碼器和解碼器指定後援物件。

> [!NOTE]
> Unicode 標準會對每個受支援字集中的每個字元，指派一個字碼指標 (數字) 和一個名稱。 例如，字元 "A" 是由字碼指標 U+0041 和名稱 "LATIN CAPITAL LETTER A" 來表示。 Unicode 轉換格式 (UTF) 編碼定義將字碼指標編碼為一或多個位元組序列的方式。 Unicode 編碼配置簡化全球化應用程式的開發作業，因為它能夠以單一編碼表示任何字元集的字元。 應用程式開發人員不再需要追蹤用來產生特定語言或書寫系統字元的編碼配置，同時資料可在各國系統之間共用，而不會損毀。
>
>  .NET 支援由 Unicode 標準定義的三種編碼：UTF-8、UTF-16 和 UTF-32。 如需詳細資訊，請參閱 [Unicode](http://www.unicode.org/) 首頁的＜Unicode Standard＞。
 
.NET 支援下表所列的字元編碼系統。

編碼 | 類別 | 描述 | 優點/缺點
-------- | ----- | ----------- | ------------------------ 
ASCII | [ASCIIEncoding](xref:System.Text.ASCIIEncoding) | 使用位元組較低的七個位元編碼有限範圍的字元。 | 由於這個編碼僅支援 U+0000 到 U+007F 之間的字元值，因此大部分的情況下並不適用於國際化的應用程式。
UTF-7 | [UTF7Encoding](xref:System.Text.UTF7Encoding) | 以 7 位元 ASCII 字元序列表示字元。 非 ASCII 的 Unicode 字元則以 ASCII 字元的逸出序列表示。 | UTF-7 支援通訊協定，例如電子郵件和新聞群組通訊協定。 不過，UTF-7 並沒有特別安全或穩固。 在某些情況下，變更一個位元便可能會徹底改變整個 UTF-7 字串的解譯。 而在其他情況下，不同的 UTF-7 字串可能會編碼為相同的文字。 對於包含非 ASCII 字元的序列而言，UTF-7 比 UTF-8 需要更多空間，而且編碼/解碼的速度比較慢。 因此，您應該盡可能使用 UTF-8，而不是 UTF-7。
UTF-8 | [UTF8Encoding](xref:System.Text.UTF8Encoding) | 以一到四個位元組的序列表示每個 Unicode 字碼指標。 | UTF-8 支援 8 位元的資料大小，而且適用於許多現有的作業系統。 對於 ASCII 字元範圍而言，UTF-8 與 ASCII 編碼完全相同，而且允許範圍更廣的字元集。 不過，針對中日韓 (CJK) 字集，UTF-8 可能要求每個字元需有三個位元組，而且造成的資料大小可能比 UTF-16 還大。 請注意，ASCII 資料量 (例如 HTML 標記) 有時可能是 CJK 範圍大小增加的原因。
UTF-16 | [UnicodeEncoding](xref:System.Text.UnicodeEncoding) | 以一個或兩個 16 位元整數的序列表示每個 Unicode 字碼指標。 雖然 Unicode 補充字元 (U+10000 及以上) 需要兩個 UTF-16 Surrogate 字碼指標，但最常用的 Unicode 字元只需要一個 UTF-16 字碼指標。 同時支援位元組由小到大和位元組由大到小的位元組順序。 | Common Language Runtime 會使用 UTF-16 編碼表示 Char 和 String 值，而 Windows 作業系統會使用該編碼表示 WCHAR 值。
UTF-32 | [UTF32Encoding](xref:System.Text.UTF32Encoding) | 以 32 位元整數表示每個 Unicode 字碼指標。 同時支援位元組由小到大和位元組由大到小的位元組順序。 | 當編碼空間對作業系統十分重要，而應用程式想要在作業系統上避免 UTF-16 編碼的 Surrogate 字碼指標行為時，可以使用 UTF-32 編碼。 畫面上呈現的單一字符仍然可以使用一個以上的 UTF-32 字元編碼。

這些編碼可讓您處理 Unicode 字元，以及舊版應用程式中最常用的編碼。 此外，您可以藉由定義衍生自 [Encoding](xref:System.Text.Encoding) 的類別及覆寫其成員，來建立自訂編碼。

> [!NOTE]
> 根據預設，除了字碼頁 28591 以及UTF-8 和 UTF-16 等 Unicode 編碼之外，.NET Core 不會提供任何字碼頁編碼。 不過，您可以將在以 .NET Framework 為目標的標準 Windows 應用程式中找到的字碼頁編碼，加入您的應用程式。 如需完整資訊，請參閱 [EncodingProvider](xref:System.Text.EncodingProvider) 主題。 

## <a name="selecting-an-encoding-class"></a>選取編碼類別

如果您有機會選擇應用程式使用的編碼，則應該使用 Unicode 編碼，最好是 [UTF8Encoding](xref:System.Text.UTF8Encoding) 或 [UnicodeEncoding](xref:System.Text.UnicodeEncoding) (.NET 也支援第三種 Unicode 編碼 [UTF32Encoding](xref:System.Text.UTF32Encoding))。 

如果您打算使用 ASCII 編碼 ([ASCIIEncoding](xref:System.Text.ASCIIEncoding))，請改為選擇 [UTF8Encoding](xref:System.Text.UTF8Encoding)。 這兩種編碼對於 ASCII 字元集而言完全相同，但是 [UTF8Encoding](xref:System.Text.UTF8Encoding) 具有下列優點： 

* 它可以表示每個 Unicode 字元，而 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 只支援 U+0000 與 U+007F 之間的 Unicode 字元值。

* 它提供錯誤偵測且具有較佳的安全性。

* 它已調整成其可能的最快速度，因此在速度上應該會超過其他任何編碼。 即使為全部都是 ASCII 的內容，使用 [UTF8Encoding](xref:System.Text.UTF8Encoding) 執行的作業也會快過使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 執行的作業。

您應該考慮只對舊版應用程式使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding)。 不過，即使是舊版應用程式，[UTF8Encoding](xref:System.Text.UTF8Encoding) 仍然可能是較佳的選擇，原因如下 (假設使用預設值)：

* 如果您的應用程式具有的內容不完全是 ASCII，而且使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 編碼該內容，則每個非 ASCII 字元都會編碼為問號 (?)。 如果應用程式接著解碼這份資料，資訊就會遺失。


* 如果應用程式具有的內容不完全是 ASCII，而且使用 [UTF8Encoding](xref:System.Text.UTF8Encoding) 編碼該內容，將結果解譯為 ASCII 會難以理解。 不過，如果應用程式接著使用 UTF-8 解碼器來解碼這份資料，則該資料會成功地執行來回轉換。

在 Web 應用程式中，傳送至用戶端以回應 Web 要求的字元應該反映用戶端上使用的編碼。 在大部分情況下，您應該將 [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) 屬性設定為 [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) 屬性所傳回的值，以便以使用者預期的編碼來顯示文字。

## <a name="using-an-encoding-object"></a>使用編碼物件

編碼器會將字元字串 (最常見為 Unicode 字元) 轉換成其對等數值 (位元組)。 例如，您可能使用 ASCII 編碼器將 Unicode 字元轉換成 ASCII，以便在主控台上顯示。 若要執行轉換，請呼叫 [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) 方法。 如果您想要在執行編碼之前判斷儲存編碼的字元需要多少個位元組，可以呼叫 [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) 方法。

下列範例會在兩項不同的作業中使用單一位元組陣列編碼字串。 它會保留一個索引，指出下一組 ASCII 編碼位元組在位元組陣列中的開始位置。 它會呼叫 [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) 方法，確保位元組陣列的大小夠大，足以容納編碼的字串。 然後它會呼叫 [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) 方法來編碼字串中的字元。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

解碼器會將反映特定字元編碼的位元組陣列轉換成字元陣列或字串中的字元集。 若要將位元組陣列解碼為字元陣列，請呼叫 [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 方法。 若要將位元組陣列解碼為字串，請呼叫 [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) 方法。 如果您想要在執行解碼之前判斷儲存解碼的位元組需要多少個字元，可以呼叫 [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) 方法。

下列範例會編碼三個字串，然後將這些字串解碼為單一字元陣列。 它會保留一個索引，指出下一組解碼的字元在字元陣列中的開始位置。 它會呼叫 [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) 方法，確保字元陣列的大小夠大，足以容納所有解碼的字元。 然後它會呼叫 [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法來解碼位元組陣列。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

衍生自 [Encoding](xref:System.Text.Encoding) 之類別的編碼和解碼方法設計成可處理一組完整的資料；也就是說，單一方法呼叫中會提供所有要編碼或解碼的資料。 不過，在某些情況下，資料是以資料流提供，因此只能從個別讀取作業取得要編碼或解碼的資料。 因此，編碼或解碼作業必須記住之前叫用時的任何儲存狀態。 衍生自 [Encoder](xref:System.Text.Encoder) 和 [Decoder](xref:System.Text.Decoder) 之類別的方法能夠處理橫跨多個方法呼叫的編碼和解碼作業。

特定編碼的 [Encoder](xref:System.Text.Encoder) 物件可從該編碼的 [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) 屬性取得。 特定編碼的 [Decoder](xref:System.Text.Decoder) 物件可從該編碼的 [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) 屬性取得。 若為解碼作業，請注意衍生自 [Decoder](xref:System.Text.Decoder) 的類別包含 [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法，但是沒有對應至 [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])) 的方法。

下列範例說明使用 [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 和 [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法解碼 Unicode 位元組陣列的差異。 這個範例會將包含某些 Unicode 字元的字串編碼為檔案，然後使用這兩種解碼方法進行解碼，且一次解碼十個位元組。 由於 Surrogate 字組會在第十個和第十一個位元組發生，因此會在不同的方法呼叫中另外解碼。 如輸出所示，[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 方法無法正確解碼位元組，而是將它們取代為 U+FFFD (REPLACEMENT CHARACTER)。 另一方面，[Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法能夠成功解碼位元組陣列並取得原始字串。

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a>選擇後援策略

當某個方法嘗試編碼或解碼字元，但是沒有任何對應存在時，它就必須實作後援策略，以決定應該如何處理失敗的對應。 後援策略有三種類型： 

* 自動調整後援

* 取代後援

* 例外狀況後援

> [!IMPORTANT]
> 編碼作業最常在 Unicode 字元無法對應至特定字碼頁編碼時發生問題。 解碼作業最常在無效的位元組序列無法轉譯為有效的 Unicode 字元時發生問題。 因此，您應該知道特定編碼物件所使用的後援策略。 您應該在執行個體化編碼物件時，盡可能指定該物件所使用的後援策略。
 
### <a name="bestfit-fallback"></a>自動調整後援

當字元在目標編碼中沒有完全相符的字元時，編碼器可以嘗試將該字元對應至類似的字元 (自動調整後援大部分是針對編碼問題，而不是針對解碼問題。 很少有字碼頁包含無法成功對應至 Unicode 的字元)。自動調整後援是 [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) 和 [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) 多載所擷取之字碼頁和雙位元組字元集編碼的預設值。

> [!NOTE]
> 理論上，.NET 中提供的 Unicode 編碼類別 ([UTF8Encoding](xref:System.Text.UTF8Encoding)、[UnicodeEncoding](xref:System.Text.UnicodeEncoding) 和 [UTF32Encoding](xref:System.Text.UTF32Encoding)) 支援每個字元集中的每個字元，因此這些類別可以用來解決自動調整後援的問題。 
 

自動調整策略會因不同的字碼頁而異，並且沒有詳細的說明。 例如，某些字碼頁的全形拉丁字元會對應至更常見的半形拉丁字元。 至於其他字碼頁，則不會進行這項對應。 即使有主動的自動調整策略，還是會有些字元在特定編碼中沒有適當的對應。 例如，中文表意字元在字碼頁 1252 中便沒有適當的對應。 在這種情況下，會使用取代字串。 根據預設，這個字串只是單一 QUESTION MARK (U+003F)。

下列範例會使用字碼頁 1252 (西歐語言的 Windows 字碼頁) 說明自動調整對應及其缺點。 [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) 方法可用來為字碼頁 1252 擷取編碼物件。 根據預設，它會針對不支援的 Unicode 字元使用自動調整對應。 這個範例會執行個體化包含三個非 ASCII 字元的字串：CIRCLED LATIN CAPITAL LETTER S (U+24C8)、SUPERSCRIPT FIVE (U+2075) 和 INFINITY (U+221E) (以空格分隔)。 如範例的輸出所示，編碼字串時，這三個原始非空格字元會被 QUESTION MARK (U+003F)、DIGIT FIVE (U+0035) 和 DIGIT EIGHT (U+0038) 取代。 DIGIT EIGHT 對於不支援的 INFINITY 字元來說，是相當差的取代，QUESTION MARK 則表示沒有可供原始字元使用的對應。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

自動調整對應是 [Encoding](xref:System.Text.Encoding) 物件的預設行為，可將 Unicode 資料編碼為字碼頁資料，有些舊版應用程式需要這個行為。 不過，基於安全性理由，大多數的新應用程式都應該避免自動調整行為。 例如，應用程式不應該透過自動調整編碼方式放入定義域名稱。

> [!Note]
> 您也可以實作編碼的自訂自動調整後援對應。 如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。
 
如果自動調整後援是編碼物件的預設值，則當您藉由呼叫 [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) 或 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 多載擷取 [Encoding](xref:System.Text.Encoding) 物件時，可以選擇其他後援策略。 下節範例會以星號 (\*)取代每一個 對應到字碼頁 1252 的字元。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a>取代後援

當字元在目標配置中沒有完全相符的字元，但是沒有可以對應的適當字元時，應用程式就可以指定取代字元或字串。 這是 Unicode 解碼器的預設行為，該行為會將任何無法解碼的兩個位元組序列取代為 REPLACEMENT_CHARACTER (U+FFFD)。 它也是 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 類別的預設行為，該行為會將任何無法編碼或解碼的每個字元取代為問號。 下列範例說明前一個範例中 Unicode 字串的字元取代。 如輸出所示，每個無法解碼為 ASCII 位元組值的字元都會以 0x3F 取代，也就是以問號取代 ASCII 碼。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

.NET 包含 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 和 [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) 類別，這兩個類別會在字元無法於編碼或解碼作業中精確對應時替代取代字串。 根據預設，這個取代字串會是一個問號，但是您可以呼叫類別建構函式多載，以便選擇不同的字串。 取代字串通常 (但不一定) 是單一字元。 下列範例會具現化使用星號 (\*) 作為取代字串的 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 物件，變更字碼頁 1252 編碼器的行為。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> 您也可以實作編碼的取代類別。 如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。
 
除了 QUESTION MARK (U+003F) 之外，還常使用 Unicode REPLACEMENT CHARACTER (U+FFFD) 做為取代字串，特別是當解碼無法成功轉譯成 Unicode 字元的位元組序列時。 不過，您可以自由選擇任何取代字串，而且該字串可以包含多個字元。

### <a name="exception-fallback"></a>例外狀況後援

編碼器可在無法編碼一組字元時擲回 [EncoderFallbackException](xref:System.Text.EncoderFallbackException)，而解碼器可在無法解碼位元組陣列時擲回 [DecoderFallbackException](xref:System.Text.DecoderFallbackException)，而不是提供自動調整後援或取代字串。 若要在編碼和解碼作業中擲回例外狀況，請將 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 物件和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件分別提供給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法。 下列範例說明 ASCIIEncoding 類別的例外狀況後援。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> 您也可以實作編碼作業的自訂例外狀況處理常式。 如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。
 
[EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件提供下列造成例外狀況之條件的相關資訊： 

* [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 物件包含 [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) 方法，這個方法會指出無法編碼的一或多個字元代表未知的 Surrogate 字組 (在這種情況下，方法會傳回 `true`)，或未知的單一字元 (在這種情況下，方法會傳回 `false`)。 Surrogate 字組中的字元可從 [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) 和 [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) 屬性取得。 未知的單一字元可從 [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) 屬性取得。 [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) 屬性會指出字串中找到第一個無法編碼之字元的位置。

* [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件包含 [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) 屬性，這個屬性會傳回無法解碼的位元組陣列。 [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) 屬性會指出未知位元組的開始位置。

雖然 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件提供了有關例外狀況的適當診斷資訊，但是並未提供編碼或解碼緩衝區的存取權。 因此，這兩個物件不允許在編碼或解碼方法內取代或更正無效的資料。

## <a name="implementing-a-custom-fallback-strategy"></a>實作自訂後援策略

除了字碼頁在內部實作的自動調整對應之外，.NET 還包括下列實作後援策略的類別：

* 使用 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 和 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 取代編碼作業中的字元。

* 使用 [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 取代解碼作業中的字元。

* 在無法編碼字元時，使用 [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) 和 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 擲回 [EncoderFallbackException](xref:System.Text.EncoderFallbackException)。

* 在無法解碼字元時，使用 [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 擲回 [DecoderFallbackException](xref:System.Text.DecoderFallbackException)。

此外，您可以執行下列步驟，來實作使用自動調整後援、取代後援或例外狀況後援的自訂方案： 

1. 針對編碼作業從 [EncoderFallback](xref:System.Text.EncoderFallback) 衍生類別，並針對解碼作業從 [DecoderFallback](xref:System.Text.DecoderFallback) 衍生類別。

2. 針對編碼作業從 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 衍生類別，並針對解碼作業從 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 衍生類別。

3. 至於例外狀況後援，如果預先定義的 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 類別不符合您的需求，則從例外狀況物件 (例如 [Exception](xref:System.Exception) 或 [ArgumentException](xref:System.ArgumentException)) 衍生類別。

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>衍生自 EncoderFallback 或 DecoderFallback

若要實作自訂後援方案，您必須針對編碼作業建立繼承自 [EncoderFallback](xref:System.Text.EncoderFallback) 的類別，以及針對解碼作業建立繼承自 [DecoderFallback](xref:System.Text.DecoderFallback) 的類別。 這些類別的執行個體會傳遞給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法，並且作為編碼類別和後援實作之間的媒介。

當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：

* [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) 或 [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) 屬性，這個屬性會傳回自動調整、取代或例外狀況後援可傳回以取代單一字元的最大字元數。 若是自訂例外狀況後援，其值為零。 

* [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) 或 [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) 方法，這個方法會傳回您自訂的 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 或 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 實作。 編碼器會在遇到無法成功編碼的第一個字元時呼叫這個方法，而解碼器會在遇到無法成功解碼的第一個位元組時呼叫這個方法。

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>衍生自 EncoderFallbackBuffer 或 DecoderFallbackBuffer

若要實作自訂後援方案，您還必須針對編碼作業建立繼承自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 的類別，以及針對解碼作業建立繼承自 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 的類別。 這些類別的執行個體會由 [EncoderFallback](xref:System.Text.EncoderFallback) 和 [DecoderFallback](xref:System.Text.DecoderFallback) 類別的 `CreateFallbackBuffer` 方法傳回。 編碼器會在遇到無法編碼的第一個字元時呼叫 [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) 方法，而解碼器會在遇到無法解碼的一或多個位元組時呼叫 [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) 方法。 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 類別提供後援實作。 每個執行個體代表包含後援字元的緩衝區，這些後援字元將取代無法編碼的字元或無法解碼的位元組序列。

當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：

* [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) 或 [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) 方法。 編碼器會呼叫 [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) 來提供後援緩衝區，其中包含無法編碼之字元的相關資訊。 由於要編碼的字元可能是 Surrogate 字組，因此這個方法為多載。 其中一個多載會收到傳遞之要編碼的字元，以及其在字串中的索引。 第二個多載會收到傳遞的高和低 Surrogate，以及其在字串中的索引。 解碼器會呼叫 [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) 方法來提供後援緩衝區，其中包含無法解碼之位元組的相關資訊。 這個方法會收到傳遞之無法解碼的位元組陣列，以及第一個位元組的索引。 如果後援緩衝區可以提供自動調整或一或多個取代字元，則後援方法應該傳回 `true`，否則應該傳回 `false`。 若是例外狀況後援，後援方法應該擲回例外狀況。

* [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) 或 [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) 方法，編碼器或解碼器會重複呼叫這個方法，以便從後援緩衝區取得下一個字元。 當所有後援字元都已傳回時，這個方法應傳回 U+0000。 

* [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) 或 [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) 屬性，這個屬性會傳回後援緩衝區中剩餘的字元數。

* [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) 或 [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) 方法，這個方法會將後援緩衝區中的目前位置移至前一個字元。

* [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) 或 [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) 方法，這個方法會重新初始化後援緩衝區。

如果後援實作是自動調整後援或取代後援，則衍生自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 的類別還會維護兩個私用執行個體欄位：緩衝區中確實的字元數，以及緩衝區中要傳回之下一個字元的索引。

### <a name="an-encoderfallback-example"></a>EncoderFallback 範例

前文中的範例使用了取代後援，以星號 (\*) 取代無法對應到 ASCII 字元的 Unicode 字元。 下列範例使用自訂自動調整後援實作，而不是提供較佳的非 ASCII 字元對應。

下列程式碼會定義名為 `CustomMapper` 的類別，該類別衍生自 [EncoderFallback](xref:System.Text.EncoderFallback)，會處理非 ASCII 字元的自動調整對應。 其 `CreateFallbackBuffer` 方法會傳回提供 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 實作的 `CustomMapperFallbackBuffer` 物件。 `CustomMapper` 類別使用 [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) 物件來儲存不支援的 Unicode 字元對應 (機碼值) 及其對應的 8 位元字元 (儲存在 64 位元整數的兩個連續的位元組中)。 為了讓後援緩衝區可以使用這項對應，`CustomMapper` 執行個體會當做參數傳遞給 `CustomMapperFallbackBuffer` 類別建構函式。 由於最長的對應是代表 Unicode 字元 U+221E 的字串 "INF"，因此 `MaxCharCount` 屬性會傳回 3。 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

下列程式碼會定義 `CustomMapperFallbackBuffer` 類別，該類別衍生自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。 包含自動調整對應並在 `CustomMapper` 執行個體中定義的字典可從其類別建構函式取得。 如果 ASCII 編碼器無法編碼的任何 Unicode 字元是在對應字典中定義，則其 `Fallback` 方法會傳回 `true`，否則會傳回 `false`。 針對每個後援，私用 `count` 變數會指出要傳回的剩餘字元數，而私用 `index` 變數會指出要傳回的下一個字元在字串緩衝區 `charsToReturn` 中的位置。 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

接著，下列程式碼會執行個體化 `CustomMapper` 物件，並將該物件的執行個體傳遞給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法。 輸出會指出，自動調整後援實作成功處理原始字串中這三個非 ASCII 字元。

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a>請參閱

[System.Text.Encoder](xref:System.Text.Encoder)

[System.Text.EncoderFallback](xref:System.Text.EncoderFallback)

[System.Text.Decoder](xref:System.Text.Decoder)

[System.Text.DecoderFallback](xref:System.Text.DecoderFallback)

[System.Text.Encoding](xref:System.Text.Encoding)







<!--HONumber=Nov16_HO1-->


