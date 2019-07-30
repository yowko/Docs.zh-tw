---
title: .NET Framework 應用程式中的 COM 互通性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 758f065d2e0e7f8200529ef171dc89f94950b46e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627085"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="1b5d6-102">.NET Framework 應用程式中的 COM 互通性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b5d6-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>

<span data-ttu-id="1b5d6-103">當您想要在相同的應用程式中使用 COM 物件和 .NET Framework 物件時, 您必須解決物件存在於記憶體中的差異。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="1b5d6-104">.NET Framework 物件位於 managed 記憶體中 (由 common language runtime 所控制的記憶體), 而且可以視需要由執行時間移動。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="1b5d6-105">COM 物件位於非受控記憶體中, 因此不應該移至另一個記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="1b5d6-106">Visual Studio 和 .NET Framework 提供工具來控制這些受控和非受控元件的互動。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-106">Visual Studio and the .NET Framework provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="1b5d6-107">如需 managed 程式碼的詳細資訊, 請參閱[Common Language Runtime](../../../standard/clr.md)。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>

<span data-ttu-id="1b5d6-108">除了在 .NET 應用程式中使用 COM 物件, 您可能也會想要使用 Visual Basic 來開發可透過 COM 從非受控程式碼存取的物件。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>

<span data-ttu-id="1b5d6-109">此頁面上的連結提供 COM 和 .NET Framework 物件之間互動的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1b5d6-110">相關章節</span><span class="sxs-lookup"><span data-stu-id="1b5d6-110">Related sections</span></span>

| | |
|---------|---------|
| [<span data-ttu-id="1b5d6-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="1b5d6-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md) | <span data-ttu-id="1b5d6-112">提供涵蓋 Visual Basic 中 COM 互通性主題的連結, 包括 COM 物件、ActiveX 控制項、Win32 Dll、managed 物件, 以及 COM 物件的繼承。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span> |
| [<span data-ttu-id="1b5d6-113">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="1b5d6-113">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md) | <span data-ttu-id="1b5d6-114">簡短描述 managed 和非受控碼之間的一些互動問題, 並提供進一步研究的連結。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-114">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span> |
| [<span data-ttu-id="1b5d6-115">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="1b5d6-115">COM Wrappers</span></span>](../../../standard/native-interop/com-wrappers.md) | <span data-ttu-id="1b5d6-116">討論執行時間可呼叫包裝函式, 其可讓 managed 程式碼呼叫 COM 方法和 COM 可呼叫包裝函式, 以允許 COM 用戶端呼叫 .NET 物件方法。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-116">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span> |
| [<span data-ttu-id="1b5d6-117">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="1b5d6-117">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md) | <span data-ttu-id="1b5d6-118">提供主題連結, 其中包含與包裝函式、例外狀況、繼承、執行緒、事件、轉換和封送處理相關的 COM 互通性。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-118">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span> |
| [<span data-ttu-id="1b5d6-119">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="1b5d6-119">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md) | <span data-ttu-id="1b5d6-120">討論您可以用來將 COM 類型程式庫中找到的類型定義轉換成 common language runtime 元件中的對等定義的工具。</span><span class="sxs-lookup"><span data-stu-id="1b5d6-120">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span> |
