---
title: 已建立內嵌 Interop 組件 '<assembly1>' 的參考，因為該組件的間接參考來自組件 '<assembly2>'。
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: c0b4f56e3d1613486dd1198976557831ce657e1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774855"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="3e426-102">已建立內嵌 interop 組件參考 '\<assembly1 >' 因為該組件的間接參考來自組件'\<assembly2 >'</span><span class="sxs-lookup"><span data-stu-id="3e426-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="3e426-103">已建立內嵌 Interop 組件 '\<assembly1>' 的參考，因為該組件的間接參考來自組件 '\<assembly2>'。</span><span class="sxs-lookup"><span data-stu-id="3e426-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="3e426-104">請考慮變更其中任何一個組件上的 [內嵌 Interop 類型] 屬性。</span><span class="sxs-lookup"><span data-stu-id="3e426-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="3e426-105">您已新增組件 (assembly1) 的參考，該組件的 `Embed Interop Types` 屬性已設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="3e426-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="3e426-106">這會指示編譯器內嵌該組件中的 Interop 類型資訊。</span><span class="sxs-lookup"><span data-stu-id="3e426-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="3e426-107">不過，編譯器無法內嵌該組件中的 Interop 類型資訊，因為您所參考的另一個組件 (assembly2) 也在參考該組件 (assembly1)，而且其 `Embed Interop Types` 屬性已設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3e426-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e426-108">將組件參考的 `Embed Interop Types` 屬性設定為 `True`，相當於使用命令列編譯器的 `/link` 選項。</span><span class="sxs-lookup"><span data-stu-id="3e426-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="3e426-109">**錯誤 ID:** BC40059</span><span class="sxs-lookup"><span data-stu-id="3e426-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="3e426-110">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="3e426-110">To address this warning</span></span>  
  
- <span data-ttu-id="3e426-111">若要同時內嵌這兩個組件的 Interop 類型資訊，請將所有 assembly1 參考的 `Embed Interop Types` 屬性都設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="3e426-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
- <span data-ttu-id="3e426-112">若要移除警告，您可以將 assembly1 的 `Embed Interop Types` 屬性設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3e426-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="3e426-113">在此情況下，主要 interop 組件 (PIA) 所提供的 interop 類型資訊。</span><span class="sxs-lookup"><span data-stu-id="3e426-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e426-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e426-114">See also</span></span>

- [<span data-ttu-id="3e426-115">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e426-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="3e426-116">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="3e426-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
