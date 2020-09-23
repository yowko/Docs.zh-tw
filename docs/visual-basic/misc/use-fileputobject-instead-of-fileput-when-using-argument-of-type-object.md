---
title: 使用類型 'Object' 的引數時，請以 'FilePutObject' 代替 'FilePut'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100330"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="1da8b-102">使用類型 'Object' 的引數時，請以 'FilePutObject' 代替 'FilePut'</span><span class="sxs-lookup"><span data-stu-id="1da8b-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="1da8b-103">`FilePut` 方法包含類型 `Object`的引數。</span><span class="sxs-lookup"><span data-stu-id="1da8b-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="1da8b-104">`FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="1da8b-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1da8b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1da8b-105">To correct this error</span></span>  
  
- <span data-ttu-id="1da8b-106">將 `FilePut` 取代為 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="1da8b-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="1da8b-107">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="1da8b-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="1da8b-108">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="1da8b-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da8b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1da8b-109">See also</span></span>

- [<span data-ttu-id="1da8b-110">我的電腦. 檔案系統</span><span class="sxs-lookup"><span data-stu-id="1da8b-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="1da8b-111">My.user. My.computer.filesystem.writeallbytes</span><span class="sxs-lookup"><span data-stu-id="1da8b-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
