---
title: 檔案太大，無法讀入位元組陣列中
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831510"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>檔案太大，無法讀入位元組陣列中
您嘗試讀取的位元組陣列的檔案大小超過 4 GB。 `My.Computer.FileSystem.ReadAllBytes`方法無法讀取超過此大小的檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用<xref:System.IO.StreamReader>讀取檔案。 如需詳細資訊，請參閱 <<c0> [ 基本概念的.NET Framework 檔案 I/O 和檔案系統 (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [使用 Visual Basic 存取檔案](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [如何：StreamReader 從檔案讀取文字](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
