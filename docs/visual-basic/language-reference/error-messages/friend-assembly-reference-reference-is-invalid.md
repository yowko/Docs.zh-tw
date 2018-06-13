---
title: Friend 組件參考&lt;參考&gt;無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587367"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="67441-102">Friend 組件參考&lt;參考&gt;無效</span><span class="sxs-lookup"><span data-stu-id="67441-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="67441-103">Friend 組件參考\<參考 > 無效。</span><span class="sxs-lookup"><span data-stu-id="67441-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="67441-104">以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="67441-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="67441-105">組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式識別是強式名稱組件，但它不包含`PublicKey`屬性。</span><span class="sxs-lookup"><span data-stu-id="67441-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="67441-106">**錯誤 ID:** BC31535</span><span class="sxs-lookup"><span data-stu-id="67441-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67441-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="67441-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="67441-108">判斷公開金鑰的強式名稱的 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="67441-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="67441-109">包含公開金鑰，因為組件名稱的一部分傳遞至<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式使用`PublicKey`屬性。</span><span class="sxs-lookup"><span data-stu-id="67441-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67441-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67441-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="67441-111">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="67441-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

