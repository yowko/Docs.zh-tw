---
title: "在規則運算式中執行字元逸出"
description: "在規則運算式中執行字元逸出"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 41d35531-2af9-47d4-9780-fbc1e682fbc2
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e4f4b9cde90a98215c0aaab6da217ff68476cf88

---

# <a name="character-escapes-in-regular-expressions"></a>在規則運算式中執行字元逸出

規則運算式中的反斜線 (\) 表示下列其中一： 

* 它後面所接的字元是特殊字元，如下節中的資料表所示。 例如，**\b** 是表示規則運算式比對應該在字邊界上開始的一個錨點，**\t** 代表定位字元，而 **\x020** 代表空格。

* 一個字元應該依其字面來解譯，否則會被解譯為未逸出的語言結構。 例如，大括號 (**{**) 開始定義數量詞，但反斜線後面接著一個大括號 (**\{**) 則表示規則運算式引擎應該比對大括號。 同樣地，單一反斜線標記逸出的語言建構之開頭，但兩個反斜線 (**\\**) 則表示規則運算式引擎應該比對反斜線。

> [!NOTE]
> 逸出字元會在規則運算式模式而不是在取代模式中被辨識。 
 
## <a name="character-escapes-in-net"></a>.NET 中的逸出字元

下表列出 .NET 中的規則運算式所支援的逸出字元。

字元或序列 | 描述
--------------------- | ----------- 
下列字元以外的所有字元：**. $ ^ { [ ( &#124; ) * + ? \** | 不同於列在 [字元或序列] 資料行中的其他字元在規則運算式中沒有任何特殊的意義；它們符合其本身。 [字元或序列] 資料行中所包含的字元是規則運算式的特殊語言項目。 若要在規則運算式中進行比對，它們必須逸出或包含在正字元群組。 例如，規則運算式 `\$\d+ or [$]\d+` 符合 "$1200"。 
**\a** | 符合警鈴 (警示) 字元 **\u0007**。
**\b** | 在 __[__*character*_*group*__]__ 字元類別，比對退格鍵 **\u0008** (請參閱[規則運算式中的字元類別](classes.md))。在字元類別之外，**\b** 是符合字邊界的錨點 (請參閱[規則運算式中的錨點](anchors.md))。
**\t** | 比對定位字元 **\u0009**。
**\r** | 比對歸位字元 **\u000D**。 請注意，**\r** 不等於新行字元 **\n**。
**\v** | 比對垂直定位字元 **\u000B**。
**\f** | 比對換頁字元 **\u000C**。
**\n** | 比對新行字元 **\u000A**。
**\e** | 比對逸出字元 **\u001B**。
**\**_nnn_ | 符合 ASCII 字元，其中 nnn 是由代表八進位字元碼的兩個或三個數字所組成。 例如，`\040` 代表空格字元。 其若只有一個數字 (例如 `\2`)，或其對應至擷取群組的編號，會將此建構解譯為反向參考  (請參閱[規則運算式中的反向參考建構](backreference.md))。 
**\x**_nn_ | 符合 ASCII 字元，其中 *nn* 是兩位數的十六進位字元碼。
**\c**_X_ | 符合 ASCII 控制字元，其中 *X* 是控制字元的字母。 例如，`\cC` 是 CTRL + C。
**\u**_nnnn_ | 符合 UTF-16 字碼單位，其值為十六進位的 *nnnn*。 **注意事項** .NET 不支援用來指定 Unicode 的 Perl 5 逸出字元。 Perl 5 逸出字元的形式是 **\x{####…}**，其中 **####…** 是一系列的十六進位數字。 請改用 **\u**_nnnn_。 
**\** | 當後面加上一個不被認為是逸出的字元時，符合該字元。 例如，`\*` 符合使用星號 (*)，而且與 `\x2A` 相同。
 
## <a name="example"></a>範例

下列範例說明如何在規則運算式中使用逸出字元。 它會剖析字串，包含在 2009 年世界上最大城市的名稱以及人口。 每個城市名稱及其人口數目被定位字元 (**\t**) 或分隔號 (| 或 `\u007c`) 分開。 個別的城市及其人口是被歸位字元和換行字元分隔開的。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string delimited = @"\G(.+)[\t\u007c](.+)\r?\n";
      string input = "Mumbai, India|13,922,125\t\n" + 
                            "Shanghai, China\t13,831,900\n" + 
                            "Karachi, Pakistan|12,991,000\n" + 
                            "Delhi, India\t12,259,230\n" + 
                            "Istanbul, Turkey|11,372,613\n";
      Console.WriteLine("Population of the World's Largest Cities, 2009");
      Console.WriteLine();
      Console.WriteLine("{0,-20} {1,10}", "City", "Population");
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, delimited))
         Console.WriteLine("{0,-20} {1,10}", match.Groups[1].Value, 
                                            match.Groups[2].Value);
   }
}
// The example displyas the following output:
//       Population of the World's Largest Cities, 2009
//       
//       City                 Population
//       
//       Mumbai, India        13,922,125
//       Shanghai, China      13,831,900
//       Karachi, Pakistan    12,991,000
//       Delhi, India         12,259,230
//       Istanbul, Turkey     11,372,613
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim delimited As String = "\G(.+)[\t\u007c](.+)\r?\n"
      Dim input As String = "Mumbai, India|13,922,125" + vbCrLf + _
                            "Shanghai, China" + vbTab + "13,831,900" + vbCrLf + _
                            "Karachi, Pakistan|12,991,000" + vbCrLf + _
                            "Delhi, India" + vbTab + "12,259,230" + vbCrLf + _
                            "Istanbul, Turkey|11,372,613" + vbCrLf
      Console.WriteLine("Population of the World's Largest Cities, 2009")
      Console.WriteLine()
      Console.WriteLine("{0,-20} {1,10}", "City", "Population")
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, delimited)
         Console.WriteLine("{0,-20} {1,10}", match.Groups(1).Value, _
                                            match.Groups(2).Value)
      Next                         
   End Sub
End Module
' The example displays the following output:
'       Population of the World's Largest Cities, 2009
'       
'       City                 Population
'       
'       Mumbai, India        13,922,125
'       Shanghai, China      13,831,900
'       Karachi, Pakistan    12,991,000
'       Delhi, India         12,259,230
'       Istanbul, Turkey     11,372,613
```

規則運算式 `\G(.+)[\t|\u007c](.+)\r?\n` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\G` | 從最後比對結束之處開始比對。
`(.+)` | 一或多次比對任何字元。 這是第一個擷取群組。
`[\t\u007c]` | 比對定位字元 (**\t**) 或分隔號 (&#124;)。
`(.+)` | 一或多次比對任何字元。 這是第二個擷取群組。
`\r?\n` | 比對後面接著新行的歸位字元其中的零或指定項目。
 
## <a name="see-also"></a>另請參閱

[規則運算式語言 - 快速參考](quick-ref.md)




<!--HONumber=Nov16_HO3-->


