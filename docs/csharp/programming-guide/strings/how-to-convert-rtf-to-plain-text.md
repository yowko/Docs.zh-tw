---
title: "如何：轉換 RTF 為純文字 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a>如何：轉換 RTF 為純文字 (C# 程式設計手冊)
Rich Text Format (RTF) 是 Microsoft 在 1980 年代晚期開發的文件格式，以便跨作業系統交換文件。 Microsoft Word 和 WordPad 都可以讀取和寫入 RTF 文件。 在 .NET Framework 中，您可以使用 <xref:System.Windows.Forms.RichTextBox> 控制項來建立支援 RTF 的文書處理器，讓使用者以 WYSIWIG 的方式將格式套用至文字。  
  
 您也可以使用 <xref:System.Windows.Forms.RichTextBox> 控制項，以程式設計方式移除 RTF 格式化文件中的程式碼，並將它轉換成純文字。 您不需要將控制項內嵌在 Windows Form，就能執行此類作業。  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a>在專案中使用 RichTextBox 控制項  
  
1.  新增 System.Windows.Forms.dll 的參考。  
  
2.  為 `System.Windows.Forms` 命名空間新增 using 指示詞 (選擇性)。  
  
## <a name="example"></a>範例  
 下列範例會將範例 RTF 檔轉換成純文字。 此檔案包含 RTF 格式 (例如字型資訊)、四個 Unicode 字元，以及四個延伸的 ASCII 字元。 範例程式碼會開啟檔案，將其內容傳遞至 <xref:System.Windows.Forms.RichTextBox> 為 RTF，擷取內容為文字，以 <xref:System.Windows.Forms.MessageBox> 顯示文字，再將文字輸出為 UTF-8 格式的檔案。  
  
 `MessageBox` 和輸出檔案包含下列文字：  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 RTF 字元會以八個位元編碼。 不過，使用者可在指定字碼頁的延伸 ASCII 字元之外，另行指定 Unicode 字元。 因為 <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> 屬性是[字串](../../../csharp/language-reference/keywords/string.md)類型，所以字元都會編碼為 Unicode UTF-16。 來源 RTF 文件中任何擴充的 ASCII 字元和 Unicode 字元，都會使用文字輸出正確編碼。  
  
 如果您使用 <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> 方法將文字寫入磁碟，則文字會編碼為 UTF-8 (無位元組順序標記)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [字串](../../../csharp/programming-guide/strings/index.md)

