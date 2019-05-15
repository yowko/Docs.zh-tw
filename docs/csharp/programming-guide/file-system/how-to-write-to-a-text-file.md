---
title: 作法：寫入文字檔 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: e3fa0eb12c9259629ff8151ff2d057f2744e9e36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595621"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>作法：寫入文字檔 (C# 程式設計手冊)
在下列這些範例中，會示範幾個將文字寫入檔案的方法。 前兩個範例會在 <xref:System.IO.File?displayProperty=nameWithType> 類別上使用靜態便利方法，將任何 `IEnumerable<string>` 和字串的每個項目和字串寫入文字檔。 範例 3 中會示範寫入檔案時，如何在需要分別處理每一行時，將文字加入至檔案。 範例 1-3 會覆寫檔案中所有現有的內容，但是範例 4 將示範如何將文字附加至現有的檔案。  
  
 這些範例全都會將字串常值寫入至檔案。 如果您想要格式化寫入檔案的文字，請使用 <xref:System.String.Format%2A> 方法或 C# [字串內插補點](../../../csharp/language-reference/tokens/interpolated.md)功能。  
  
## <a name="example"></a>範例  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- 該檔案存在而且是唯讀的。  
  
- 路徑名稱可能太長。  
  
- 磁碟可能已滿。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [檔案系統和登錄 (C# 程式設計指南)](../../../csharp/programming-guide/file-system/index.md)
- [範例：如何將集合儲存至應用程式儲存空間](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
