---
title: "常數 (Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e086e856bb7a872b14815825f78d208ff5296899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="e4ea7-102">常數 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="e4ea7-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="e4ea7-103">本主題描述的語言類型、 語言廠商和定義於 CorSym.idl 中的文件類型常數。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="e4ea7-104">語言類型常數</span><span class="sxs-lookup"><span data-stu-id="e4ea7-104">Language Type Constants</span></span>  
 <span data-ttu-id="e4ea7-105">下表顯示類型的常數，表示 Guid，用於識別程式設計語言的語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="e4ea7-106">符號</span><span class="sxs-lookup"><span data-stu-id="e4ea7-106">Symbol</span></span>|<span data-ttu-id="e4ea7-107">描述</span><span class="sxs-lookup"><span data-stu-id="e4ea7-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e4ea7-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="e4ea7-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="e4ea7-109">表示 C 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="e4ea7-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="e4ea7-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="e4ea7-111">表示 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="e4ea7-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="e4ea7-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="e4ea7-113">表示 C# 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="e4ea7-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="e4ea7-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="e4ea7-115">表示基本語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="e4ea7-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="e4ea7-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="e4ea7-117">表示 Java 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="e4ea7-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="e4ea7-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="e4ea7-119">表示 COBOL 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="e4ea7-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="e4ea7-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="e4ea7-121">表示依照 pascal 命名法的語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="e4ea7-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="e4ea7-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="e4ea7-123">表示 Microsoft intermediate language (MSIL) 的組譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="e4ea7-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="e4ea7-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="e4ea7-125">表示 JScript 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="e4ea7-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="e4ea7-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="e4ea7-127">表示讓 SMC 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="e4ea7-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="e4ea7-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="e4ea7-129">表示啟用.NET Framework 的 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="e4ea7-130">語言廠商常數</span><span class="sxs-lookup"><span data-stu-id="e4ea7-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="e4ea7-131">下表顯示的語言廠商常數，代表用來識別程式設計的語言廠商 Guid。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="e4ea7-132">符號</span><span class="sxs-lookup"><span data-stu-id="e4ea7-132">Symbol</span></span>|<span data-ttu-id="e4ea7-133">描述</span><span class="sxs-lookup"><span data-stu-id="e4ea7-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e4ea7-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4ea7-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="e4ea7-135">表示 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="e4ea7-136">文件類型常數</span><span class="sxs-lookup"><span data-stu-id="e4ea7-136">Document Type Constants</span></span>  
 <span data-ttu-id="e4ea7-137">下表顯示文件類型的常數，表示用來識別文件類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="e4ea7-138">符號</span><span class="sxs-lookup"><span data-stu-id="e4ea7-138">Symbol</span></span>|<span data-ttu-id="e4ea7-139">描述</span><span class="sxs-lookup"><span data-stu-id="e4ea7-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e4ea7-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="e4ea7-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="e4ea7-141">表示文字文件。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="e4ea7-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="e4ea7-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="e4ea7-143">表示非文字文件。</span><span class="sxs-lookup"><span data-stu-id="e4ea7-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4ea7-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4ea7-144">See Also</span></span>  
 [<span data-ttu-id="e4ea7-145">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="e4ea7-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
