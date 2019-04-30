---
title: .NET Framework 應用程式中的 COM 互通性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 6e8b4eba40cc1872cb289ca120679bb951f2652a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022373"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="aff33-102">.NET Framework 應用程式中的 COM 互通性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff33-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>

<span data-ttu-id="aff33-103">當您想要在相同的應用程式中使用 COM 物件和.NET Framework 物件時，您需要解決的物件存在於記憶體中的差異。</span><span class="sxs-lookup"><span data-stu-id="aff33-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="aff33-104">.NET Framework 物件位於 managed 記憶體 — common language runtime 所控制的記憶體，並可以由執行階段移動，視需要。</span><span class="sxs-lookup"><span data-stu-id="aff33-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="aff33-105">COM 物件位在 unmanaged 記憶體，且不應該將移至另一個記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="aff33-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="aff33-106">Visual Studio 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。</span><span class="sxs-lookup"><span data-stu-id="aff33-106">Visual Studio and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="aff33-107">如需有關 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](../../../standard/clr.md)。</span><span class="sxs-lookup"><span data-stu-id="aff33-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>

<span data-ttu-id="aff33-108">除了.NET 應用程式中使用 COM 物件，您可能也想要使用 Visual Basic 來開發可從 unmanaged 程式碼，透過 COM 存取的物件</span><span class="sxs-lookup"><span data-stu-id="aff33-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>

<span data-ttu-id="aff33-109">此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aff33-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="aff33-110">相關章節</span><span class="sxs-lookup"><span data-stu-id="aff33-110">Related sections</span></span>

| | |
|---------|---------|
| [<span data-ttu-id="aff33-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="aff33-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md) | <span data-ttu-id="aff33-112">提供連結，這些主題涵蓋在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll，受管理的物件，以及繼承的 COM 物件的 COM 互通性。</span><span class="sxs-lookup"><span data-stu-id="aff33-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span> |
| [<span data-ttu-id="aff33-113">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="aff33-113">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md) | <span data-ttu-id="aff33-114">簡要說明一些 managed 和 unmanaged 程式碼之間的互動問題，並提供進一步的研究的連結。</span><span class="sxs-lookup"><span data-stu-id="aff33-114">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span> |
| [<span data-ttu-id="aff33-115">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="aff33-115">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md) | <span data-ttu-id="aff33-116">討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="aff33-116">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span> |
| [<span data-ttu-id="aff33-117">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="aff33-117">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md) | <span data-ttu-id="aff33-118">提供涵蓋相對於包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換和封送處理 COM 互通性的主題連結。</span><span class="sxs-lookup"><span data-stu-id="aff33-118">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span> |
| [<span data-ttu-id="aff33-119">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="aff33-119">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md) | <span data-ttu-id="aff33-120">討論您可以用來轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。</span><span class="sxs-lookup"><span data-stu-id="aff33-120">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span> |