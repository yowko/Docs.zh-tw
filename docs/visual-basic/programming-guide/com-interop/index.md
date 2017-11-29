---
title: COM Interop (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c87852024412b7a7ed55a2c429842ce75a13a8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="794b6-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="794b6-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="794b6-103">元件物件模型 (COM) 可讓物件向其他元件公開其功能以及主控應用程式。</span><span class="sxs-lookup"><span data-stu-id="794b6-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="794b6-104">大部分的現今軟體都會包括 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="794b6-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="794b6-105">雖然 .NET 組件是新應用程式的最佳選擇，但您有時可能需要採用 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="794b6-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="794b6-106">本節涵蓋一些與使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 建立和使用 COM 物件建立關聯的問題。</span><span class="sxs-lookup"><span data-stu-id="794b6-106">This section covers some of the issues associated with creating and using COM objects with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="794b6-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="794b6-107">In This Section</span></span>  
 [<span data-ttu-id="794b6-108">COM Interop 簡介</span><span class="sxs-lookup"><span data-stu-id="794b6-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="794b6-109">提供 COM 互通性的概觀。</span><span class="sxs-lookup"><span data-stu-id="794b6-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="794b6-110">如何：參考 Visual Basic 的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="794b6-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="794b6-111">涵蓋如何將參考新增至具有型別程式庫的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="794b6-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="794b6-112">操作說明：使用 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="794b6-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="794b6-113">示範如何使用現有 ActiveX 控制項來新增 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 工具箱的功能。</span><span class="sxs-lookup"><span data-stu-id="794b6-113">Demonstrates how to use existing ActiveX controls to add features to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Toolbox.</span></span>  
  
 [<span data-ttu-id="794b6-114">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="794b6-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="794b6-115">逐步解說如何呼叫屬於 Windows 作業系統之 API 的程序。</span><span class="sxs-lookup"><span data-stu-id="794b6-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="794b6-116">操作說明：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="794b6-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="794b6-117">示範如何在 User32.dll 中定義和呼叫 `MessageBox` 函式。</span><span class="sxs-lookup"><span data-stu-id="794b6-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="794b6-118">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="794b6-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="794b6-119">示範如何呼叫具有不帶正負號類型之參數的 Windows 函式。</span><span class="sxs-lookup"><span data-stu-id="794b6-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="794b6-120">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="794b6-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="794b6-121">逐步解說如何在使用和不使用 COM 類別範本的情況下建立 COM 物件的程序。</span><span class="sxs-lookup"><span data-stu-id="794b6-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="794b6-122">互通性的疑難排解</span><span class="sxs-lookup"><span data-stu-id="794b6-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="794b6-123">涵蓋您可能在使用 COM 時發生的一些問題。</span><span class="sxs-lookup"><span data-stu-id="794b6-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="794b6-124">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="794b6-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="794b6-125">概述如何在相同的應用程式中使用 COM 物件和 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="794b6-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="794b6-126">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="794b6-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="794b6-127">描述如何使用現有 COM 物件作為新物件的基礎。</span><span class="sxs-lookup"><span data-stu-id="794b6-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="794b6-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="794b6-128">Related Sections</span></span>  
 [<span data-ttu-id="794b6-129">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="794b6-129">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="794b6-130">描述 Common Language Runtime 提供的互通性服務。</span><span class="sxs-lookup"><span data-stu-id="794b6-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="794b6-131">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="794b6-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="794b6-132">描述如何透過 COM Interop 呼叫 COM 類型的程序。</span><span class="sxs-lookup"><span data-stu-id="794b6-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="794b6-133">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="794b6-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="794b6-134">描述如何從 COM 準備和使用 Managed 類型。</span><span class="sxs-lookup"><span data-stu-id="794b6-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="794b6-135">套用 Interop 屬性</span><span class="sxs-lookup"><span data-stu-id="794b6-135">Applying Interop Attributes</span></span>](https://msdn.microsoft.com/library/d4w8x20h)  
 <span data-ttu-id="794b6-136">涵蓋您可以在處理 Unmanaged 程式碼時使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="794b6-136">Covers attributes you can use when working with unmanaged code.</span></span>
