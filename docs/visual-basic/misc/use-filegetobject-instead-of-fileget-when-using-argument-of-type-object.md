---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723390"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="44ec2-102">使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'</span><span class="sxs-lookup"><span data-stu-id="44ec2-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="44ec2-103">`FileGet` 方法包含類型 `Object`的引數。</span><span class="sxs-lookup"><span data-stu-id="44ec2-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="44ec2-104">`FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="44ec2-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="44ec2-105">請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。</span><span class="sxs-lookup"><span data-stu-id="44ec2-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="44ec2-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="44ec2-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="44ec2-107">將 `FileGet` 取代為 `FileGetObject`。</span><span class="sxs-lookup"><span data-stu-id="44ec2-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="44ec2-108">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="44ec2-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ec2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44ec2-109">See also</span></span>

- [<span data-ttu-id="44ec2-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="44ec2-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
