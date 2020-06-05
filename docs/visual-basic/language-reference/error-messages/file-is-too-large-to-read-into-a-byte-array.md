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
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="e284d-102">檔案太大，無法讀入位元組陣列中</span><span class="sxs-lookup"><span data-stu-id="e284d-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="e284d-103">您嘗試讀入位元組陣列的檔案大小超過 4 GB。</span><span class="sxs-lookup"><span data-stu-id="e284d-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="e284d-104">`My.Computer.FileSystem.ReadAllBytes`方法無法讀取超過此大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="e284d-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e284d-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e284d-105">To correct this error</span></span>  
  
- <span data-ttu-id="e284d-106">使用 <xref:System.IO.StreamReader> 來讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="e284d-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="e284d-107">如需詳細資訊，請參閱[.NET Framework 檔案 i/o 和檔案系統的基本概念（Visual Basic）](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e284d-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e284d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e284d-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="e284d-109">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="e284d-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="e284d-110">作法：以 StreamReader 從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="e284d-110">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
