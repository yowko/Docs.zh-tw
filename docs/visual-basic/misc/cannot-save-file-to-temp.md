---
title: 無法將檔案儲存至 TEMP
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID735
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3196f5f70405c6bf7ab8eda3d056c5a86eca57f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-save-file-to-temp"></a><span data-ttu-id="1fb2d-102">無法將檔案儲存至 TEMP</span><span class="sxs-lookup"><span data-stu-id="1fb2d-102">Cannot save file to TEMP</span></span>
<span data-ttu-id="1fb2d-103">元件找不到名為 TEMP 的目錄，或包含 TEMP 目錄的磁碟機或磁碟分割的空間不足，無法儲存資訊。</span><span class="sxs-lookup"><span data-stu-id="1fb2d-103">Either a component cannot find a directory named TEMP, or the drive or partition containing the TEMP directory lacks sufficient space to save information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1fb2d-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1fb2d-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="1fb2d-105">建立名為 "TEMP" 的目錄，並設定等於其路徑的 TEMP 環境變數。</span><span class="sxs-lookup"><span data-stu-id="1fb2d-105">Create a directory named "TEMP" and set the TEMP environment variable equal to its path.</span></span>  
  
2.  <span data-ttu-id="1fb2d-106">清除不必要的檔案來清出磁碟機上的空間，或在另一個磁碟分割上建立 TEMP 目錄，並設定等於其路徑的 TEMP 環境變數。</span><span class="sxs-lookup"><span data-stu-id="1fb2d-106">Make space on the drive by erasing unnecessary files, or create a TEMP directory on another partition and set the TEMP environment variable equal to its path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb2d-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fb2d-107">See Also</span></span>  
 [<span data-ttu-id="1fb2d-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="1fb2d-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
