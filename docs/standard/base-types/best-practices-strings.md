---
title: "使用字串的最佳做法"
description: "使用字串的最佳做法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e

---

# <a name="best-practices-for-using-strings"></a>使用字串的最佳做法

.NET 可廣泛支援當地語系化和全球化應用程式的開發作業，使您在執行一般作業 (例如排序和顯示字串) 時，可輕鬆套用目前的文化特性或特定文化特性的慣例。 但是，排序或比較字串並不一定是區分文化特性的作業。 例如，應用程式內部使用的字串，通常應該跨所有文化特性皆進行相同處理。 若將與文化特性無關的字串資料 (例如 XML 標記、HTML 標記、使用者名稱、檔案路徑和系統物件的名稱) 進行區分文化特性的解譯時，應用程式程式碼可能會出現細微的 Bug、效能不佳，甚至在某些情況下，會產生安全性問題。

本文會詳述 .NET 中的字串排序、比較和大小寫方法，並提供適當字串處理方法的選擇建議，以及字串處理方法的其他資訊。 它也會說明如何處理數值資料和日期與時間資料之類的格式化資料，以供顯示及儲存。 

本文包含下列章節：

* [字串的使用建議](#recommendations-for-string-usage)

* [明確指定字串比較](#specifying-string-comparisons-explicitly)

* [字串比較的詳細資料](#the-details-of-string-comparison)

* [為您的方法呼叫選擇 StringComparison 成員](#choosing-a-stringcomparison-member-for-your-method-call)

* [常用的字串比較方法](#common-string-comparison-methods)

* [間接執行字串比較的方法](#methods-that-perform-string-comparison-indirectly)

* [顯示及保存格式化的資料](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a>字串的使用建議

當您使用 .NET 進行開發時，請遵循下列簡單的字串使用建議： 

* 使用明確指定字串比較規則的多載來進行字串作業。 一般而言，這需要呼叫具有 [StringComparison](xref:System.StringComparison) 類型參數的方法多載。

* 將 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 作為安全的無從驗證文化特性字串預設比對，來進行比較。

* 使用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 來比較以提升效能。

* 向使用者顯示輸出時，您可以使用依據 [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) 的字串作業。

* 在進行語言無關的比較 (如符號) 時，使用非語言式 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 值，而不是依據 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 的字串作業。

* 正規化字串以進行比較，使用 [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) 方法，而非 [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) 方法。

* 使用 [String](xref:System.String) `Equals` 方法的多載，來測試兩個字串是否相等。

* 使用 [String](xref:System.String) `Compare` 和 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法的多載來排序字串，而不檢查是否相等。

* 使用區分文化特性的格式來顯示使用者介面中的非字串資料，例如數字和日期。 使用不因文化特性而異的格式來保存字串形式的非字串資料。

當您使用字串時，請避免下列作法：

* 不要使用未明確或未隱含指定字串比較規則的多載來進行字串作業。 

* 不要使用 [String](xref:System.String) `Compare` 或 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法的多載以及傳回零值的測試，來判斷兩個字串是否相等。

* 不要使用區分文化特性的格式來保存數值資料或字串形式的日期和時間資料。

## <a name="specifying-string-comparisons-explicitly"></a>明確指定字串比較

在 .NET 中的字串操作方法大多都是多載。 一般而言，您可讓一或多個多載接受預設值，而其他不接受預設值的多載，則定義用來比較或操作字串的精確方式。 大部分不依賴預設值的方法都會包含 [StringComparison](xref:System.StringComparison) 類型的參數，其為一種列舉，可明確指定依據文化特性和大小寫進行字串比較的規則。 下表說明 [StringComparison](xref:System.StringComparison) 列舉成員。 

StringComparison 成員 | 說明
----------------------- | -----------
[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) | 使用目前文化特性執行區分大小寫的比較。
[CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) | 使用目前文化特性執行不區分大小寫的比較。
[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) | 執行序數比較。
[StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) | 執行不區分大小寫的序數比較。

例如，[String](xref:System.String) `IndexOf` 方法有下列九個多載，可傳回 [String](xref:System.String) 物件中符合某字元或某字串之子字串的索引：

* [IndexOf(Char)](xref:System.String.IndexOf(System.Char))、[IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)) 和 [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)) 預設會執行字串字元的序數 (區分大小寫且區分文化特性) 搜尋。

* [IndexOf(String)](xref:System.String.IndexOf(System.String))、[IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)) 和 [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)) 預設會執行字串的子字串搜尋 (區分大小寫且區分文化特性)。

* [IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison))、[IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)) 和 [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison))，包括 StringComparison 類型的參數，可指定比較形式。

基於下列原因，建議您選取不使用預設值的多載：

* 有些使用預設參數的多載 (其會在字串執行個體中搜尋 [Char](xref:System.Char)) 會執行序數比較，而其他多載 (其會搜尋字串執行個體中的字串) 有區分文化特性。 使用者很難記住哪一種方法使用預設值，也很容易混淆多載。

* 依賴預設值來執行方法呼叫的程式碼意圖並不清楚。 在下列依賴預設值的範例中，我們很難知道開發人員到底要進行兩個字串的序數或語言比較，也很難判斷 `protocol` 和 "http" 之間的大小寫差異是否會造成相等測試傳回 `false`。

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

一般而言，我們建議您呼叫不依賴預設值的方法，因為它會讓程式碼的意圖不明確。 不過，這可讓程式碼更容易閱讀也更容易偵錯與維護。 下列範例將解決先前範例所引發的問題。 它會清楚指出使用序數比較，並且忽略大小寫差異。 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a>字串比較的詳細資料

字串比較是許多字串相關作業的核心，尤其是排序和測試是否相等這類作業。 字串依固定順序排序：在已排序的字串清單中，如果 "my" 在 "string" 之前出現，則 "my" 比較起來一定小於或等於 "string"。 此外，比較也隱含定義相等性。 比較作業會針對它認為相等的字串傳回零。 明言之，就是沒有任一字串比另一個字串更小。 最有意義的字串作業包含下列一或兩個程序：和其他字串進行比較，並執行定義完善的排序作業。

不過，評估兩個字串是否相等或決定排序順序不會產生單一的正確結果，而要取決於用來比較字串的準則而定。 特別是，如果字串比較是序數或根據目前文化特性或不因文化特性而異的大小寫與排序慣例 (根據英文語言的無從驗證地區設定文化特性)，則可能會產生不同的結果。

### <a name="string-comparisons-that-use-the-current-culture"></a>使用目前之文化特性的字串比較

比較字串時，其中一個準則需使用目前文化特性的慣例。 如果比較是以目前文化特性為依據，就會使用執行緒的目前文化特性或地區設定。 當資料是語言相關資料，以及資料會反映區分文化特性的使用者互動時，請一律使用以目前文化特性為根據的比較。 

不過，當文化特性變更時，.NET 中的比較和大小寫行為也會有所變更。 當執行應用程式的電腦其文化特性不同於開發應用程式的電腦時，或執行中的執行緒變更其文化特性時，會發生這種情況。 此種行為有其用意，但對許多開發人員來說並不容易注意到。 下列範例說明美國英文 ("en-US") 和瑞典文 ("sv-SE") 文化特性之間排序次序的差異。 請注意單字 "ångström"、"Windows" 和 "Visual Studio" 出現在已排序的字串陣列中的不同位置。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

如果比較是使用目前文化特性且不區分大小寫，這類比較和區分文化特性的比較相同 (除了這些比較會忽略執行緒目前文化特性的大小寫要求以外)。 這種行為可能會以排序順序來呈現。 

下列方法預設為執行使用目前文化特性之語意的比較：

* 不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `Compare` 多載。

* [String.CompareTo](xref:System.String.CompareTo(System.String)) 多載。

* 預設 [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) 方法。 

* 預設 [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) 方法。

* 可接受 [String](xref:System.String) 作為搜尋參數且不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `IndexOf` 多載。

* 可接受 [String](xref:System.String) 作為搜尋參數且不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `LastIndexOf` 多載。

在任何情況下，都建議您呼叫具有 [StringComparison](xref:System.StringComparison) 參數的多載，以讓方法呼叫的目的更清晰。 

若以語言方式解譯非語言式的字串資料，或使用其他文化特性的慣例解譯來自特定文化特性的字串資料時，可能會出現微妙或不太微妙的 Bug。 標準範例是土耳其文 I 的問題。

對於幾乎所有拉丁字母 (包括美國英文)，字元 "i" (\u0069) 是字元 "I" (\u0049) 的小寫。 這種大小寫規則很快成為以這種文化特性進行程式設計的人所採用的預設規則。 不過，土耳其文 ("tr-TR") 字母包括「加上一點的 I」字元 "İ" (\u0130)，也就是 "i" 的大寫。 土耳其文中也包含「不含點的 i 」字元，"ı" (\u0131)，其大寫為 "I"。 亞塞拜然 ("az") 文化特性中也會發生這種行為。

因此，關於將 "i" 轉換成大寫或將 "I" 轉換成小寫的假設並不適用。 如果您針對字串比較常式使用預設多載，就會受限於文化特性之間的差異。 如果要比較的資料為非語言式，使用預設多載可能產生非預期的結果，如下列嘗試執行字串 "file" 和 "FILE" 之不區分大小寫的比較範例所示。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

如果不小心將文化特性用於安全性相關設定 (如下列範例所示)，這項比較可能會造成重大的問題。 如果目前的文化特性是美國英文，方法呼叫 (如 `IsFileURI("file:")`) 會傳回 `true`；但若目前的文化特性為土耳其文，則傳回 `false`。 因此，在土耳其文的系統中，有心人士可以使用開頭為 "FILE:" 的 URI，來規避封鎖存取不區分大小寫之 URI 的安全性措施。

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

在此情況下，由於 "file:" 應解譯為非語言式、不區分文化特性的識別項，因此程式碼應改為下列範例：

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a>序數字串作業

在方法呼叫中指定 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 值意謂著非語言比較，其中忽略自然語言的特性。 若使用這類 [StringComparison](xref:System.StringComparison) 值來叫用方法，方法就會以簡單的位元組比較來進行字串作業決策，而不以文化特性參數化的大小寫或對等項目資料表為根據。 在大部分情況下，這種方法非常適合預期的字串解譯，同時可讓程式碼更快速、可靠。 

序數比較是一種字串比較，其會比較每個字串的每個位元組，而不進行語言解譯；例如，"windows" 不符合 "Windows"。 如果內容指出字串應該完全相符，或要求保守的比對原則時，請使用這項比較。 此外，序數比較在決定結果時不會套用任何語言規則，因此是最快速的比較作業。

.NET 中的字串可以包含內嵌的 Null 字元。 序數和區分文化特性的比較 (包括使用不因文化特性而異的比較) 其中一個最明顯差異在於，內嵌 Null 字元在字串中的處理方式。 當您使用 [String](xref:System.String) `Compare` 和 [String](xref:System.String) `Equals` 方法來執行區分文化特性的比較 (包括使用不因文化特性而異的比較) 時，會忽略這些字元。 如此一來，在區分文化特性的比較中，即可將包含內嵌 Null 字元的字串視為等於不含這類字元的字串。 

> [!IMPORTANT]
> 雖然字串比較方法可以忽略內嵌的 Null 字元，但 [String.Contains](xref:System.String.Contains(System.String))、[String.EndsWith](xref:System.String.EndsWith(System.String))、[String.IndexOf](xref:System.String.IndexOf(System.Char))、[String.LastIndexOf](xref:System.String.LastIndexOf(System.String)) 和 [String.StartsWith](xref:System.String.StartsWith(System.String)) 之類的字串搜尋方法就不能這麼做了。 

下列範例會針對字串 "Aa" 以及 "A" 和 "a" 之間包含數個內嵌 Null 字元的類似字串，執行區分文化特性比較，並示範如何讓兩個字串被視為相等。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

不過，當您使用序數比較時，字串就不會被視為相等，如下列範例所示。

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

第二種最保守的方式是不區分大小寫的序數比較。 這些比較會忽略大部分的大小寫；例如，"windows" 符合 "Windows"。 當處理 ASCII 字元時，這項原則相當於 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)，不過它會忽略一般 ASCII 大小寫。 因此，[A, Z] (\u0041-\u005A) 中的任何字元會符合 [a,z] (\u0061-\007A) 中的對應字元。 ASCII 範圍之外的大小寫會使用不因文化特性而異的資料表。 因此，下列比較：

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

相當於下列比較 (而且更快)： 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

這些比較仍非常快速。

[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 和 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 兩者都直接使用二進位值，最適合用來比對。 當您不確定比較設定時，請使用這兩個值的其中一個。 不過，因為它們是以位元組為單位逐一比較，所以不會依照語言排序次序來排序 (就像英文字典一樣)，而是採用二進位排序次序。 因此，在大多數內容當中，使用者看到的結果可能很奇怪。

不包含 [StringComparison](xref:System.StringComparison) 引數 (包括等號比較運算子) 的 [String](xref:System.String) `Equals` 多載是以序數語意為預設。 在任何情況下，我們建議您呼叫具有 [StringComparison](xref:System.StringComparison) 參數的多載。

### <a name="string-operations-that-use-the-invariant-culture"></a>使用文化特性不變的字串作業

採用不因文化特性而異的比較會使用靜態 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性傳回的 [CompareInfo](xref:System.Globalization.CompareInfo) 屬性。 這種行為在所有系統上都相同，它會將其範圍之外的任何字元轉譯成它認為是相等非變異字元的字元。 這項原則很適合跨文化特性來維護一套字串行為，但通常會產生非預期的結果。

採用不因文化特性而異的不區分大小寫比較，也會使用靜態 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性所傳回的靜態 [CompareInfo](xref:System.Globalization.CompareInfo) 屬性來取得比較資訊。 這些轉譯的字元之間的任何大小寫差異都會被忽略。

[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 物件使 [String](xref:System.String) `Compare` 方法將多組字元解譯成相等。 例如，下列等式在不因國別而異的文化特性之下有效：

InvariantCulture: a + ̊ = å

拉丁小寫字母 A 字元 "a" (\u0061) 在緊鄰著結合上圓圈字元 "+ " ̊" (\u030a) 時，解譯成拉丁小寫字母 A 帶上圓圈字元 "å" (\u00e5)。 如下列範例如示，這種行為不同於序數比較。

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

在解譯檔名、Cookie 或可能出現像 "å" 一樣的組合的其他任何字串時，序數比較仍然會展現最明確和最適當的行為。

權衡來看，不因國別而異的文化特性只有非常少的屬性，因此適合用於比較。 不過，它會以語言相關的方式進行比較，這樣無法保證符號完全相等，因而不適合在任何文化特性中顯示。 例如，如果包含已排序之顯示識別項清單的大型資料檔案伴隨一個應用程式，則加入這份清單需要插入非變異樣式排序。

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>為您的方法呼叫選擇 StringComparison 成員

下表列出語意字串內容與 [StringComparison](xref:System.StringComparison) 列舉成員的對應。

資料 | 行為 | 對應的 System.StringComparison 值
---- | -------- | -------------------------------------------
區分大小寫的內部識別項、在標準中區分大小寫的識別項 (例如 XML 和 HTTP) 或區分大小寫的安全性相關設定。 | 位元組完全相符的非語言識別項。 | [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)
不區分大小寫的內部識別項、在標準中區分大小寫的識別項 (例如 XML 和 HTTP)、檔案路徑、登錄機碼和值、環境變數、資源識別項 (例如控制代碼名稱) 或不區分大小寫的安全性相關設定。 | 大小寫不重要的非語言識別項。 | [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase)
顯示給使用者的資料或大部分的使用者輸入。 | 需要當地語言自訂的資料。 | [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) 或 [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)

## <a name="common-string-comparison-methods"></a>常用的字串比較方法

下列各節描述字串比較最常用的方法。

### <a name="stringcompare"></a>String.Compare

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

由於是字串解譯最主要的作業，這些方法呼叫的所有執行個體都應該經過檢查，以決定字串應該根據目前文化特性來解譯，還是與文化特性分開 (符號形式)。 通常是後者，所以應該改用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 比較。

由 [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) 屬性傳回的 [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) 類別也包含 [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) 方法，這個方法透過 [CompareOptions](xref:System.Globalization.CompareOptions) 旗標列舉，提供大量比對選項 (序數、忽略空白字元、忽略假名類型等)。 

### <a name="stringcompareto"></a>String.CompareTo

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

這個方法目前未提供任何指定 [StringComparison](xref:System.StringComparison) 類型的多載。 通常可以將這個方法轉換成建議的 [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) 形式。

實作 [IComparable](xref:System.IComparable) 和 [IComparable&lt;T&gt;](xref:System.IComparable%601) 介面的類型會實作這個方法。 由於它不提供 [StringComparison](xref:System.StringComparison) 參數的選項，所以實作這些類型通常可讓使用者在建構函式中指定 [StringComparer](xref:System.StringComparer)。 下列範例定義 `FileName` 類別，該類別的類別建構函式包含 [StringComparer](xref:System.StringComparer) 參數。 然後在 `FileName.CompareTo` 方法中使用這個 [StringComparer](xref:System.StringComparer) 物件。

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a>String.Equals

預設解譯：[StringComparison.Ordinal](xref:System.StringComparison.Ordinal)。

[String](xref:System.String) 類別可讓您呼叫靜態或執行個體 `Equals` 方法多載，或使用靜態等號比較運算子，以測試是否相等。 多載和運算子預設會使用序數比較。 然而，即使您想要執行序數比較，我們還是建議您呼叫明確指定 [StringComparison](xref:System.StringComparison) 類型的多載，這樣可以很輕鬆在程式碼中搜尋特定的字串解譯。 

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper 和 String.ToLower

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

請小心使用這些方法，因為強制將字串轉換為大寫或小寫，通常是做為比較不區分大小寫字串時的輕微正規化。 如果是這樣，請考慮使用不區分大小寫的比較。 

您也可以使用 [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) 和 [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) 方法。 [ToUpperInvariant](xref:System.String.ToUpperInvariant) 是將大小寫正規化的標準方式。 使用 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 進行的比較在行為上由兩次呼叫所構成：在兩個字串引數上都呼叫 [ToUpperInvariant](xref:System.String.ToUpperInvariant)，然後使用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 進行比較。

特定文化特性中，也可以使用多載將表示該文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件傳遞至這個方法，以轉換為大寫和小寫。

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper 和 Char.ToLower

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

這些方法的運作類似於上一節描述的 [String.ToUpper](xref:System.String.ToUpper) 和 [String.ToLower](xref:System.String.ToLower) 方法。

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith 和 String.EndsWith

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

根據預設，這兩個方法都會執行區分文化特性的比較。

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf 和 String.LastIndexOf

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

這些方法的預設多載在執行比較時，作法並不一致。 所有包含 [Char](xref:System.Char) 參數的 [String](xref:System.String) `IndexOf` 和 [String](xref:System.String) `LastIndexOf` 方法都執行序數比較，但包含 [String](xref:System.String) 參數的預設 [String](xref:System.String) `IndexOf` 和 [String`](xref:System.String) `LastIndexOf` 方法會執行區分文化特性的比較。 

如果您呼叫 ` `IndexOf` or `LastIndexOf` 方法，並將要在目前執行個體中尋找的字串傳遞至這個方法，我們建議您呼叫明確指定 [StringComparison](xref:System.StringComparison) 類型的多載。 包含 [Char](xref:System.Char) 引數的多載不允許您指定 [StringComparison](xref:System.StringComparison) 類型。

## <a name="methods-that-perform-string-comparison-indirectly"></a>間接執行字串比較的方法

有一些以字串比較為主要作業的非字串方法會使用 [StringComparer](xref:System.StringComparer) 類型。 [StringComparer](xref:System.StringComparer) 類別包含六個靜態屬性，這些屬性會傳回 [StringComparer](xref:System.StringComparer) 執行個體，而這些執行個體的 `Compare` 方法可以執行下列類型的字串比較：

* 使用目前文化特性的區分文化特性字串比較。 這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) 屬性傳回。

* 使用目前文化特性的不區分大小寫比較。 這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) 屬性傳回。

* 序數比較。 這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.Ordinal](xref:System.StringComparer.Ordinal) 屬性傳回。 

* 不區分大小寫的序數比較。 這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) 屬性傳回。

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort 和 Array.BinarySearch

預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。

當您將任何資料儲存在集合中，或從檔案或資料庫將保存的資料讀入集合時，切換目前文化特性會使集合中的非變異失效。 [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) 方法假設要搜尋之陣列中的項目已排序。 若要排序陣列中的任何字串項目，[Array.Sort](xref:System.Array.Sort(System.Array)) 方法會呼叫 [String] `Compare` 方法來排序個別項目。 從排序陣列到搜尋其內容這段時間當中，如果文化特性變更，則使用區分文化特性的比較子可能會有危險。 例如，在下列程式碼中，儲存和擷取作業在 `Thread.CurrentThread.CurrentCulture` 屬性所隱含提供的比較子上執行。 如果文化特性在呼叫 `StoreNames` 和 `DoesNameExist` 之間可能變更，尤其是如果陣列內容在這兩個方法呼叫之間保存在某處，則二進位搜尋可能會失敗。 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

下列範例中顯示建議的變化，其中使用相同的序數 (不區分文化特性) 比較方法來排序和搜尋陣列。 在這兩個範例中，標記為 `Line A` 和 `Line B` 的程式碼行中反映程式碼變更。

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

如果跨文化特性來保存和移動這項資料，且使用排序向使用者呈現這項資料，則您可以考慮使用 `StringComparison.InvariantCulture`，這在語言上的表現會提供較佳的使用者輸出，且不受未來文化特性變更所影響。 下列範例修改前兩個範例，改用不因國別而異的文化特性來排序和搜尋陣列。

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a>集合範例：Hashtable 建構函式

第二個受到字串比較方式而影響作業的範例是雜湊字串。 

下列範例將 [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) 屬性所傳回的 [StringComparer](xref:System.StringComparer) 物件傳遞至 [Hashtable](xref:System.Collections.Hashtable) 物件，以將後者物件執行個體化。 因為衍生自 [StringComparer](xref:System.StringComparer) 的類別 [StringComparer](xref:System.StringComparer) 實作 [IEqualityComparer](xref:System.Collections.IEqualityComparer) 介面，所以其 [GetHashCode](xref:System.Collections.IEqualityComparer) 方法會用於計算雜湊表中之字串的雜湊碼。

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a>顯示及保存格式化的資料

當您向使用者顯示非字串資料 (例如數字及日期和時間) 時，請採用使用者的文化特性設定進行格式化。 根據預設，[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法和 `ToString` 方法 (數字類型與日期和時間類型) 會使用目前執行緒的文化特性進行格式化作業。 若要明確指定格式化方法應該使用目前的文化特性，您可以呼叫具有 provider 參數之格式化方法的多載，例如 [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 或 [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider))，並將 [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) 屬性傳遞給它。 

您可將非字串資料保存為二進位資料或格式化的資料。 如果您選擇將它儲存為格式化的資料，您應該呼叫包含 *provider* 參數之格式化方法的多載，並將 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性傳遞給它。 針對獨立於文化特性和機器的格式化資料，不因國別而異的文化特性可提供一致的格式。 相較之下，如果資料並非使用不因國別而異的文化特性，而是使用其他文化特性來進行格式化，這類資料的保存會有許多限制： 

* 如果在具有不同文化特性的系統上擷取資料，或者，目前系統的使用者變更目前的文化特性，並嘗試擷取資料時，該資料可能會無法使用。 

* 特定電腦上的文化特性屬性可能不同於標準值。 使用者可以隨時自訂區分文化特性的顯示設定。 因為這個緣故，使用者自訂文化特性設定之後，可能無法讀取系統上儲存的格式化資料。 格式化資料在電腦之間的可攜性可能會有更多限制。 

* 當數字或日期和時間格式的規範標準 (不論國際、地區或國家標準) 隨著時間變更時，這些變更會併入作業系統更新當中。 當格式化慣例改變時，使用先前慣例來格式化的資料可能會變成無法讀取。 

下列範例說明使用區分文化特性的格式來保存資料時產生的可攜性限制。 此範例會將日期和時間值陣列儲存至檔案。 這些值是使用英文 (美國) 文化特性的慣例來進行格式化。 當應用程式將目前執行緒文化特性變更為法文 (瑞士) 後，它會嘗試使用目前文化特性的格式化慣例來讀取儲存的值。 嘗試讀取這兩樣資料項目後，會擲回 [FormatException](xref:System.FormatException) 例外狀況，且日期陣列現在會包含兩個等於 [MinValue](xref:System.DateTime.MinValue) 的不正確項目。 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

不過，如果您在 [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 和 [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)) 的呼叫中將 [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) 屬性取代為 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture)，則保存的日期和時間資料將會成功還原，如下列輸出所示。

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a>請參閱

[操作字串](manipulating-strings.md)



<!--HONumber=Nov16_HO1-->


