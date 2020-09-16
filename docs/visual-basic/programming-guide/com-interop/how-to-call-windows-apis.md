---
title: 作法：呼叫 Windows API
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 863986e94855e02e9fd04685f7dc3e8e7f7b1cc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548061"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="0d59b-102">如何：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d59b-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="0d59b-103">這個範例 `MessageBox` 會在 user32.dll 中定義和呼叫函數，然後將字串傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="0d59b-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d59b-104">範例</span><span class="sxs-lookup"><span data-stu-id="0d59b-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="0d59b-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0d59b-105">Compile the code</span></span>  
 <span data-ttu-id="0d59b-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0d59b-106">This example requires:</span></span>  
  
- <span data-ttu-id="0d59b-107"><xref:System> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="0d59b-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0d59b-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0d59b-108">Robust Programming</span></span>  
 <span data-ttu-id="0d59b-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="0d59b-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0d59b-110">方法不是靜態、為抽象，或先前已定義過。</span><span class="sxs-lookup"><span data-stu-id="0d59b-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="0d59b-111">父類型是介面，或是 *名稱* 或 *dllName* 的長度為零。</span><span class="sxs-lookup"><span data-stu-id="0d59b-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="0d59b-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="0d59b-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="0d59b-113">*名稱*或*dllName*為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="0d59b-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="0d59b-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="0d59b-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="0d59b-115">之前已使用 `CreateType` 建立包含類型。</span><span class="sxs-lookup"><span data-stu-id="0d59b-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="0d59b-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="0d59b-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d59b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d59b-117">See also</span></span>

- [<span data-ttu-id="0d59b-118">進一步了解平台叫用</span><span class="sxs-lookup"><span data-stu-id="0d59b-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="0d59b-119">平台叫用範例</span><span class="sxs-lookup"><span data-stu-id="0d59b-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="0d59b-120">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="0d59b-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="0d59b-121">[使用反映發出定義方法](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0d59b-121">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="0d59b-122">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="0d59b-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="0d59b-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="0d59b-123">COM Interop</span></span>](index.md)
