---
title: "如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7e9a170882c4e8dbb04dc014642a28ad4365e39
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊)
下列範例示範如何使用 <xref:System.IO?displayProperty=fullName> 命名空間的 <xref:System.IO.File?displayProperty=fullName>、<xref:System.IO.Directory?displayProperty=fullName>、<xref:System.IO.FileInfo?displayProperty=fullName> 和 <xref:System.IO.DirectoryInfo?displayProperty=fullName> 類別，以同步方式複製、移動及刪除檔案和資料夾。 這些範例不提供進度列或任何其他的使用者介面。 如果您想要提供標準的進度對話方塊，請參閱[如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)。  
  
 操作多個檔案時，請使用 <xref:System.IO.FileSystemWatcher?displayProperty=fullName> 提供可讓您計算進度的事件。 另一種方法是使用平台叫用，在 Windows Shell 中呼叫與檔案有關的相關方法。 如需如何以非同步方式執行這些檔案作業的資訊，請參閱[非同步檔案 I/O](https://msdn.microsoft.com/library/kztecsys)。  
  
## <a name="example"></a>範例  
 下例示範如何複製檔案和目錄。  
  
 [!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何移動檔案和目錄。  
  
 [!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何刪除檔案和目錄。  
  
 [!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄 (C# 程式設計手冊)](index.md)   
 [如何：提供檔案作業的進度對話方塊](how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [檔案和資料流 I/O](https://msdn.microsoft.com/library/k3352a4t)   
 [一般 I/O 工作](https://msdn.microsoft.com/library/ms404278)
