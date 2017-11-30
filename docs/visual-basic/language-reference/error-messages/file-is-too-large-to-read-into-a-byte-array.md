---
title: "檔案太大，無法讀入位元組陣列中"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="13dfa-102">檔案太大，無法讀入位元組陣列中</span><span class="sxs-lookup"><span data-stu-id="13dfa-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="13dfa-103">您嘗試讀取的位元組陣列的檔案大小超過 4 GB。</span><span class="sxs-lookup"><span data-stu-id="13dfa-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="13dfa-104">`My.Computer.FileSystem.ReadAllBytes`方法無法讀取超過此大小的檔案。</span><span class="sxs-lookup"><span data-stu-id="13dfa-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13dfa-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="13dfa-105">To correct this error</span></span>  
  
-   <span data-ttu-id="13dfa-106">使用<xref:System.IO.StreamReader>讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="13dfa-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="13dfa-107">如需詳細資訊，請參閱[基本概念的.NET Framework 檔案 I/O 和檔案系統 (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。</span><span class="sxs-lookup"><span data-stu-id="13dfa-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13dfa-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13dfa-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="13dfa-109">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="13dfa-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="13dfa-110">如何：以 StreamReader 從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="13dfa-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
