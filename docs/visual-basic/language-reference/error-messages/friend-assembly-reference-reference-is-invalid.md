---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972397"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="f2ccd-102">Friend 元件參考\<參考 > 無效</span><span class="sxs-lookup"><span data-stu-id="f2ccd-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="f2ccd-103">Friend 元件參考\<參考 > 無效。</span><span class="sxs-lookup"><span data-stu-id="f2ccd-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="f2ccd-104">以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f2ccd-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="f2ccd-105">傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性（attribute）的元件名稱會識別強式名稱的元件，但不`PublicKey`包含屬性（attribute）。</span><span class="sxs-lookup"><span data-stu-id="f2ccd-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="f2ccd-106">**錯誤識別碼：** BC31535</span><span class="sxs-lookup"><span data-stu-id="f2ccd-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2ccd-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f2ccd-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f2ccd-108">判斷強式名稱 friend 元件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f2ccd-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="f2ccd-109">使用屬性，將公開金鑰包含在傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性（attribute）的元件名稱中。 `PublicKey`</span><span class="sxs-lookup"><span data-stu-id="f2ccd-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ccd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2ccd-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="f2ccd-111">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="f2ccd-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
