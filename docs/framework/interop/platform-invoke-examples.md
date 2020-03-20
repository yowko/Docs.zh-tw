---
title: 平台叫用範例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 358d1ce662d56b8c31124f4b3264ec25a0f94586
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181324"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="717b0-102">平台叫用範例</span><span class="sxs-lookup"><span data-stu-id="717b0-102">Platform Invoke Examples</span></span>
<span data-ttu-id="717b0-103">下列範例示範如何在 User32.dll 中定義和呼叫 **MessageBox** 函式，並將簡單字串傳遞為引數。</span><span class="sxs-lookup"><span data-stu-id="717b0-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="717b0-104">在這些範例中，<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位會設定為 **Auto**，讓目標平台決定字元寬度和字串封送處理。</span><span class="sxs-lookup"><span data-stu-id="717b0-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="717b0-105">如需其他範例，請參閱[使用平台叫用封送處理資料](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="717b0-105">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717b0-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="717b0-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="717b0-107">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="717b0-107">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="717b0-108">指定字元集</span><span class="sxs-lookup"><span data-stu-id="717b0-108">Specifying a Character Set</span></span>](specifying-a-character-set.md)
