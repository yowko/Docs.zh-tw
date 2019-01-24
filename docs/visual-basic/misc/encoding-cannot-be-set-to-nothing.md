---
title: 編碼不能設定為 Nothing。
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691319"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="9e66b-102">編碼不能設定為 Nothing。</span><span class="sxs-lookup"><span data-stu-id="9e66b-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="9e66b-103">讀取或寫入檔案的嘗試失敗，因為參數 `encoding` 已設定為 `Nothing` ，但需要有效的值。</span><span class="sxs-lookup"><span data-stu-id="9e66b-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="9e66b-104"><xref:System.Text.Encoding> 用來判斷在寫入檔案時要使用的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9e66b-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="9e66b-105">預設值為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9e66b-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e66b-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9e66b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9e66b-107">請為 `encoding` 參數提供有效的值。</span><span class="sxs-lookup"><span data-stu-id="9e66b-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e66b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e66b-108">See also</span></span>
- [<span data-ttu-id="9e66b-109">檔案編碼方式</span><span class="sxs-lookup"><span data-stu-id="9e66b-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="9e66b-110">從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="9e66b-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="9e66b-111">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="9e66b-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="9e66b-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="9e66b-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="9e66b-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="9e66b-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
