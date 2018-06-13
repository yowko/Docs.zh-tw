---
title: 常數 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65925b7dafb9e89433253d68327c488365674963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406265"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="50a0b-102">常數 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="50a0b-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="50a0b-103">本主題描述的語言類型、 語言廠商和定義於 CorSym.idl 中的文件類型常數。</span><span class="sxs-lookup"><span data-stu-id="50a0b-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="50a0b-104">語言類型常數</span><span class="sxs-lookup"><span data-stu-id="50a0b-104">Language Type Constants</span></span>  
 <span data-ttu-id="50a0b-105">下表顯示類型的常數，表示 Guid，用於識別程式設計語言的語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="50a0b-106">符號</span><span class="sxs-lookup"><span data-stu-id="50a0b-106">Symbol</span></span>|<span data-ttu-id="50a0b-107">描述</span><span class="sxs-lookup"><span data-stu-id="50a0b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50a0b-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="50a0b-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="50a0b-109">表示 C 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="50a0b-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="50a0b-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="50a0b-111">表示 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="50a0b-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="50a0b-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="50a0b-113">表示 C# 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="50a0b-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="50a0b-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="50a0b-115">表示基本語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="50a0b-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="50a0b-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="50a0b-117">表示 Java 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="50a0b-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="50a0b-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="50a0b-119">表示 COBOL 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="50a0b-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="50a0b-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="50a0b-121">表示依照 pascal 命名法的語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="50a0b-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="50a0b-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="50a0b-123">表示 Microsoft intermediate language (MSIL) 的組譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="50a0b-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="50a0b-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="50a0b-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="50a0b-125">表示 JScript 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="50a0b-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="50a0b-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="50a0b-127">表示讓 SMC 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="50a0b-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="50a0b-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="50a0b-129">表示啟用.NET Framework 的 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="50a0b-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="50a0b-130">語言廠商常數</span><span class="sxs-lookup"><span data-stu-id="50a0b-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="50a0b-131">下表顯示的語言廠商常數，代表用來識別程式設計的語言廠商 Guid。</span><span class="sxs-lookup"><span data-stu-id="50a0b-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="50a0b-132">符號</span><span class="sxs-lookup"><span data-stu-id="50a0b-132">Symbol</span></span>|<span data-ttu-id="50a0b-133">描述</span><span class="sxs-lookup"><span data-stu-id="50a0b-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50a0b-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="50a0b-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="50a0b-135">表示 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="50a0b-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="50a0b-136">文件類型常數</span><span class="sxs-lookup"><span data-stu-id="50a0b-136">Document Type Constants</span></span>  
 <span data-ttu-id="50a0b-137">下表顯示文件類型的常數，表示用來識別文件類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="50a0b-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="50a0b-138">符號</span><span class="sxs-lookup"><span data-stu-id="50a0b-138">Symbol</span></span>|<span data-ttu-id="50a0b-139">描述</span><span class="sxs-lookup"><span data-stu-id="50a0b-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50a0b-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="50a0b-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="50a0b-141">表示文字文件。</span><span class="sxs-lookup"><span data-stu-id="50a0b-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="50a0b-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="50a0b-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="50a0b-143">表示非文字文件。</span><span class="sxs-lookup"><span data-stu-id="50a0b-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50a0b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50a0b-144">See Also</span></span>  
 [<span data-ttu-id="50a0b-145">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="50a0b-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
