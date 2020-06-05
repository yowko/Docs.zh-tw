---
title: 檔案太大，無法讀入位元組陣列中
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363120"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>檔案太大，無法讀入位元組陣列中
您嘗試讀入位元組陣列的檔案大小超過 4 GB。 `My.Computer.FileSystem.ReadAllBytes`方法無法讀取超過此大小的檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用 <xref:System.IO.StreamReader> 來讀取檔案。 如需詳細資訊，請參閱[.NET Framework 檔案 i/o 和檔案系統的基本概念（Visual Basic）](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [使用 Visual Basic 存取檔案](../../developing-apps/programming/drives-directories-files/file-access.md)
- [作法：以 StreamReader 從檔案讀取文字](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
