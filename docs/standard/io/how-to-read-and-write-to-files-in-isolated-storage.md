---
title: HOW TO：讀取和寫入隔離儲存區中的檔案
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59a89aa354941b7ff22a125a980c2d9c75ac37ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491515"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>HOW TO：讀取和寫入隔離儲存區中的檔案
若要在隔離存放區中的檔案內進行讀取或寫入，請使用具有資料流讀取器 (<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> 物件) 或資料流寫入器 (<xref:System.IO.StreamReader> 物件) 的 <xref:System.IO.StreamWriter> 物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會取得隔離存放區，並檢查存放區中是否存在名為 TestStore.txt 的檔案。 如果不存在，它會建立檔案，並將 "Hello Isolated Storage" 寫入檔案。 如果 TestStore.txt 已經存在，程式碼範例會從檔案讀取。  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
- [隔離儲存區](../../../docs/standard/io/isolated-storage.md)
