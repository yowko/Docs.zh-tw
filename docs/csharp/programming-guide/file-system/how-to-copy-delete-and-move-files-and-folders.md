---
title: "如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊)
下列範例會示範如何使用 <xref:System.IO?displayProperty=nameWithType> 命名空間的 <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType> 和 <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> 類別，以同步方式複製、移動和刪除檔案與資料夾。 這些範例不提供進度列或任何其他的使用者介面。 如果您想要提供標準的進度對話方塊，請參閱[如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)。  
  
 操作多個檔案時，使用 <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> 提供可讓您計算進度的事件。 另一種方法是使用平台叫用，在 Windows Shell 中呼叫與檔案有關的相關方法。 如需如何以非同步方式執行這些檔案作業的資訊，請參閱[非同步檔案 I/O](https://msdn.microsoft.com/library/kztecsys)。  
  
## <a name="example"></a>範例  
 下例示範如何複製檔案和目錄。  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何移動檔案和目錄。  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何刪除檔案和目錄。  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [檔案系統和登錄 (C# 程式設計指南)](index.md)  
 [如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [檔案和資料流 I/O](https://msdn.microsoft.com/library/k3352a4t)  
 [一般 I/O 工作](https://msdn.microsoft.com/library/ms404278)
