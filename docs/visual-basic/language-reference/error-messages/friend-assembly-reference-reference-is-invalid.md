---
title: Friend 組件參考 <reference> 無效
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160707"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="f7a4d-102">BC31535： Friend 元件參考 \<reference> 無效</span><span class="sxs-lookup"><span data-stu-id="f7a4d-102">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="f7a4d-103">Friend 元件參考 \<reference> 無效。</span><span class="sxs-lookup"><span data-stu-id="f7a4d-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="f7a4d-104">以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f7a4d-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="f7a4d-105">傳遞給 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性（attribute）的元件名稱會識別強式名稱的元件，但不包含屬性（ `PublicKey` attribute）。</span><span class="sxs-lookup"><span data-stu-id="f7a4d-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="f7a4d-106">**錯誤識別碼：** BC31535</span><span class="sxs-lookup"><span data-stu-id="f7a4d-106">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f7a4d-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f7a4d-107">To correct this error</span></span>

1. <span data-ttu-id="f7a4d-108">判斷強式名稱 friend 元件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f7a4d-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="f7a4d-109">使用屬性，將公開金鑰納入傳遞給屬性函式的元件名稱中 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="f7a4d-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a4d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a4d-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="f7a4d-111">Friend 元件</span><span class="sxs-lookup"><span data-stu-id="f7a4d-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
