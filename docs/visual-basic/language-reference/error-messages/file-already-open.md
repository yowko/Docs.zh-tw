---
title: 檔案已經開啟
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874178"
---
# <a name="file-already-open"></a><span data-ttu-id="39294-102">檔案已經開啟</span><span class="sxs-lookup"><span data-stu-id="39294-102">File already open</span></span>

<span data-ttu-id="39294-103">有時候必須先關閉檔案，才能 `FileOpen` 進行其他或其他操作。</span><span class="sxs-lookup"><span data-stu-id="39294-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="39294-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="39294-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="39294-105">已針對已開啟的檔案執行連續輸出模式作業 `FileOpen`</span><span class="sxs-lookup"><span data-stu-id="39294-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="39294-106">語句指的是開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="39294-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39294-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="39294-107">To correct this error</span></span>  
  
1. <span data-ttu-id="39294-108">請先關閉檔案，再執行語句。</span><span class="sxs-lookup"><span data-stu-id="39294-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39294-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39294-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
