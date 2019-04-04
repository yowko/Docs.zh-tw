---
title: 互通性 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 50f2a72bf4981a49d5597a9bc8922db81197d810
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411339"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="657ff-102">互通性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="657ff-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="657ff-103">互通性可讓您保留並充分利用目前在 Unmanaged 程式碼上的投資。</span><span class="sxs-lookup"><span data-stu-id="657ff-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="657ff-104">在 Common Language Runtime (CLR) 控制下執行的程式碼稱為「Managed 程式碼」，而在 CLR 外部執行的程式碼稱為「Unmanaged 程式碼」。</span><span class="sxs-lookup"><span data-stu-id="657ff-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="657ff-105">COM、COM+、C++ 元件、ActiveX 元件及 Microsoft Windows API 都是 Unmanaged 程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="657ff-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="657ff-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 會透過平台叫用服務、<xref:System.Runtime.InteropServices> 命名空間、C++ 的互通性及 COM 互通性 (COM Interop)，啟用與 Unmanaged 程式碼的互通性。</span><span class="sxs-lookup"><span data-stu-id="657ff-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="657ff-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="657ff-107">In This Section</span></span>  
 [<span data-ttu-id="657ff-108">互通性概觀</span><span class="sxs-lookup"><span data-stu-id="657ff-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="657ff-109">說明要在 C# Managed 程式碼和 Unmanaged 程式碼之間相互操作的方法。</span><span class="sxs-lookup"><span data-stu-id="657ff-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="657ff-110">如何：使用 Visual C# 功能存取 Office Interop 物件</span><span class="sxs-lookup"><span data-stu-id="657ff-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="657ff-111">說明在 Visual C# 中引進以利 Office 程式設計的功能。</span><span class="sxs-lookup"><span data-stu-id="657ff-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="657ff-112">如何：在 COM Interop 程式設計中使用已編製索引的屬性</span><span class="sxs-lookup"><span data-stu-id="657ff-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="657ff-113">說明如何使用已索引的屬性來存取具有參數的 COM 屬性。</span><span class="sxs-lookup"><span data-stu-id="657ff-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="657ff-114">如何：使用平台叫用播放 WAV 檔</span><span class="sxs-lookup"><span data-stu-id="657ff-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="657ff-115">說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="657ff-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="657ff-116">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="657ff-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="657ff-117">示範如何建立 Excel 活頁簿以及包含對該活頁簿之連結的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="657ff-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="657ff-118">範例 COM 類別</span><span class="sxs-lookup"><span data-stu-id="657ff-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="657ff-119">示範如何將 C# 類別公開為 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="657ff-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="657ff-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="657ff-120">C# Language Specification</span></span>  

<span data-ttu-id="657ff-121">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[基本概念](~/_csharplang/spec/unsafe-code.md)。</span><span class="sxs-lookup"><span data-stu-id="657ff-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="657ff-122">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="657ff-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="657ff-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="657ff-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="657ff-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="657ff-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="657ff-125">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="657ff-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)
- [<span data-ttu-id="657ff-126">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="657ff-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
