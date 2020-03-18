---
title: 如何從文字檔讀取 - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705011"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>如何從文字檔讀取（C# 程式設計指南）
這個範例會使用 <xref:System.IO.File?displayProperty=nameWithType> 類別中的靜態方法 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A>，來讀取文字檔的內容。  
  
有關 使用<xref:System.IO.StreamReader>的示例，請參閱[如何一次讀取一行文字檔](./how-to-read-a-text-file-one-line-at-a-time.md)。
  
> [!NOTE]
> 本示例中使用的檔在主題["如何寫入文字檔"](./how-to-write-to-a-text-file.md)中創建。
  
## <a name="example"></a>範例  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 將程式碼複製並貼到 C# 主控台應用程式中。  
  
如果不使用["如何寫入文字檔"](./how-to-write-to-a-text-file.md)中的文字檔，請將 參數替換為`ReadAllText`電腦上的相應路徑和檔`ReadAllLines`名，並將其替換為
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
- 檔案不存在或不在指定的位置。 請檢查路徑和檔案名稱的拼字。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請勿依賴檔案的名稱來判斷檔案的內容。 例如，`myFile.cs` 檔案可能不是 C# 原始程式檔。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO?displayProperty=nameWithType>
- [C# 程式設計指南](../index.md)
- [檔案系統和登錄 (C# 程式設計手冊)](./index.md)
