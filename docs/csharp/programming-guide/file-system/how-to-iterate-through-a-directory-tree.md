---
title: 作法：逐一查看目錄樹狀 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: ec48b9ff5a9ebe352bf0361b9e52ee0fb48576a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923972"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>作法：逐一查看目錄樹狀 (C# 程式設計手冊)
「逐一查看樹狀目錄」一詞，代表存取指定根資料夾下每個巢狀子目錄中任意深度的每個檔案。 您不需要開啟每個檔案。 您可以只擷取的檔案名稱或子目錄當成 `string`，或者可以擷取格式為 <xref:System.IO.FileInfo?displayProperty=nameWithType> 或 <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> 物件的其他資訊。  
  
> [!NOTE]
> 在 Windows 中，「目錄」和「資料夾」等詞可交替使用。 大多數文件和使用者介面文字都使用「資料夾」一詞，但 .NET Framework 類別庫則是使用「目錄」一詞。  
  
 在最簡單的情況下，當您確定具有指定根資料夾下所有目錄的存取權限時，就可以使用 `System.IO.SearchOption.AllDirectories` 旗標。 此旗標會傳回符合指定模式的所有巢狀子目錄。 下列範例示範如何使用此旗標。  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 這樣做有一個缺點，那就是指定根資料夾下若有任何一個子目錄造成 <xref:System.IO.DirectoryNotFoundException> 或 <xref:System.UnauthorizedAccessException>，整個方法就會失敗，而且不會傳回任何目錄。 當您使用 <xref:System.IO.DirectoryInfo.GetFiles%2A> 方法時，也同樣如此。 如果必須對特定子資料夾處理這些例外狀況，您必須手動查核樹狀目錄，如下列範例所示。  
  
 當您手動查核樹狀目錄時，您可以先處理子目錄 (「前序走訪」  )，或是先處理檔案 (「後序走訪」  )。 如果您執行前序走訪，您會先查核目前資料夾下的整個樹狀，再逐一查看直接位於該資料夾本身中的檔案。 本文件稍後的範例會執行後序走訪，但您可以輕鬆地修改以執行前序走訪。  
  
 另一個選項是要使用以遞迴或堆疊為基礎的走訪。 本文件稍後的範例會示範這兩種方法。  
  
 如果您必須對檔案和資料夾執行各式各樣的作業，您可以藉由將作業重構到個別函式中以模組化這些範例，這樣就可以使用單一委派來叫用這些函式。  
  
> [!NOTE]
> NTFS 檔案系統可以包含「連接點」  、「符號連結」  和「永久連結」  形式的「重新分析點」  。 .NET Framework 方法，如 <xref:System.IO.DirectoryInfo.GetFiles%2A> 和 <xref:System.IO.DirectoryInfo.GetDirectories%2A>，不會傳回重新分析點下的任何子目錄。 此行為可防止兩個重新分析點彼此參考時進入無限迴圈的風險。 一般而言，處理重新分析點要特別謹慎，以免不小心修改或刪除檔案。 如果您需要精確控制重新分析點，請使用平台叫用或機器碼，直接呼叫適當的 Win32 檔案系統方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用遞迴來查核樹狀目錄。 遞迴是很簡潔的方法，但在樹狀目錄很大且巢狀結構很深時，可能會造成堆疊溢位例外狀況。  
  
 這裡所處理的特定例外狀況，以及對每個檔案或資料夾所執行的特定動作，僅供示範之用。 您應該修改此程式碼，以符合特定需求。 如需詳細資訊，請參閱程式碼中的註解。  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>範例  
 下列範例示範如何在不使用遞迴的情況下，逐一查看樹狀目錄中的所有檔案和資料夾。 這項技術使用泛型 <xref:System.Collections.Generic.Stack%601> 集合類型，也就是後進先出 (LIFO) 堆疊。  
  
 這裡所處理的特定例外狀況，以及對每個檔案或資料夾所執行的特定動作，僅供示範之用。 您應該修改此程式碼，以符合特定需求。 如需詳細資訊，請參閱程式碼中的註解。  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 測試每個資料夾來判斷應用程式是否有權開啟資料夾，通常非常耗時。 因此，程式碼範例只會將該部分的作業封入 `try/catch` 區塊中。 您可以修改 `catch` 區塊，以便您在存取資料夾遭拒時，可以嘗試評估權限，然後重新進行存取。 一般而言，您只會攔截可處理的例外狀況，而不會讓應用程式處於未知狀態。  
  
 如果您必須儲存樹狀目錄的內容，不論是儲存在記憶體或磁碟中，最好的做法就是只儲存每個檔案的 <xref:System.IO.FileSystemInfo.FullName%2A> 屬性 (類型為 `string`)。 然後，您可以視需要使用此字串建立新的 <xref:System.IO.FileInfo> 或 <xref:System.IO.DirectoryInfo> 物件，或是開啟任何需要其他處理的檔案。  
  
## <a name="robust-programming"></a>穩固程式設計  
 設計穩固的檔案逐一查看程式碼時，必須考慮檔案系統的許多複雜情況。 如需 Windows 檔案系統的詳細資訊，請參閱 [NTFS 概觀](/windows-server/storage/file-server/ntfs-overview)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO>
- [LINQ 和檔案目錄](../concepts/linq/linq-and-file-directories.md)
- [檔案系統和登錄 (C# 程式設計指南)](./index.md)
