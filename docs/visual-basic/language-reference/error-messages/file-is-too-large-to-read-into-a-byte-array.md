---
title: 檔案太大，無法讀入位元組陣列中
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800876"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="a0ba1-102">檔案太大，無法讀入位元組陣列中</span><span class="sxs-lookup"><span data-stu-id="a0ba1-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="a0ba1-103">您嘗試讀取的位元組陣列的檔案大小超過 4 GB。</span><span class="sxs-lookup"><span data-stu-id="a0ba1-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="a0ba1-104">`My.Computer.FileSystem.ReadAllBytes`方法無法讀取超過此大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="a0ba1-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0ba1-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a0ba1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a0ba1-106">使用<xref:System.IO.StreamReader>讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="a0ba1-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="a0ba1-107">如需詳細資訊，請參閱 <<c0> [ 基本概念的.NET Framework 檔案 I/O 和檔案系統 (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ba1-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ba1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0ba1-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="a0ba1-109">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="a0ba1-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="a0ba1-110">如何：StreamReader 從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="a0ba1-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
