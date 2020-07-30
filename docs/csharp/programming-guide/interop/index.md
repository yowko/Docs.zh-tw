---
title: 互通性 - C# 程式設計手冊
description: 互通性支援在 common language runtime 底下執行的程式碼旁邊的非受控碼。 使用這些資源來瞭解 interop 選項。
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302967"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="18c1e-104">互通性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="18c1e-104">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="18c1e-105">互通性可讓您保留並充分利用目前在 Unmanaged 程式碼上的投資。</span><span class="sxs-lookup"><span data-stu-id="18c1e-105">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="18c1e-106">在 Common Language Runtime (CLR) 控制下執行的程式碼稱為「Managed 程式碼」**，而在 CLR 外部執行的程式碼稱為「Unmanaged 程式碼」**。</span><span class="sxs-lookup"><span data-stu-id="18c1e-106">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="18c1e-107">COM、COM+、C++ 元件、ActiveX 元件及 Microsoft Windows API 都是 Unmanaged 程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="18c1e-107">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="18c1e-108">.NET 透過平台叫用服務、 <xref:System.Runtime.InteropServices> 命名空間、c + + 互通性及 COM 互通性（COM Interop），啟用與非受控程式碼的互通性。</span><span class="sxs-lookup"><span data-stu-id="18c1e-108">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18c1e-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="18c1e-109">In This Section</span></span>  
 [<span data-ttu-id="18c1e-110">互通性概觀</span><span class="sxs-lookup"><span data-stu-id="18c1e-110">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="18c1e-111">說明要在 C# Managed 程式碼和 Unmanaged 程式碼之間相互操作的方法。</span><span class="sxs-lookup"><span data-stu-id="18c1e-111">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="18c1e-112">如何使用 C# 功能存取 Office Interop 物件</span><span class="sxs-lookup"><span data-stu-id="18c1e-112">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="18c1e-113">說明在 Visual C# 中引進以利 Office 程式設計的功能。</span><span class="sxs-lookup"><span data-stu-id="18c1e-113">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="18c1e-114">如何在 COM Interop 程式設計中使用已編製索引的屬性</span><span class="sxs-lookup"><span data-stu-id="18c1e-114">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="18c1e-115">說明如何使用已索引的屬性來存取具有參數的 COM 屬性。</span><span class="sxs-lookup"><span data-stu-id="18c1e-115">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="18c1e-116">如何使用平台叫用播放 WAV 檔</span><span class="sxs-lookup"><span data-stu-id="18c1e-116">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="18c1e-117">說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="18c1e-117">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="18c1e-118">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="18c1e-118">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="18c1e-119">示範如何建立 Excel 活頁簿以及包含對該活頁簿之連結的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="18c1e-119">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="18c1e-120">範例 COM 類別</span><span class="sxs-lookup"><span data-stu-id="18c1e-120">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="18c1e-121">示範如何將 C# 類別公開為 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="18c1e-121">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="18c1e-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="18c1e-122">C# Language Specification</span></span>  

<span data-ttu-id="18c1e-123">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的[基本概念](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="18c1e-123">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="18c1e-124">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="18c1e-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="18c1e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18c1e-125">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="18c1e-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="18c1e-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18c1e-127">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="18c1e-127">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="18c1e-128">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="18c1e-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
