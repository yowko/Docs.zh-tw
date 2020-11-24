---
title: 常數 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
ms.openlocfilehash: 19defe9c6c19bc04eb3c9ddaee386ef1ee409de5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673926"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="fcca3-102">常數 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="fcca3-102">Constants (Unmanaged API Reference)</span></span>

<span data-ttu-id="fcca3-103">本主題說明 CorSym 中定義的語言類型、語言廠商和檔案類型常數。</span><span class="sxs-lookup"><span data-stu-id="fcca3-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="fcca3-104">語言類型常數</span><span class="sxs-lookup"><span data-stu-id="fcca3-104">Language Type Constants</span></span>  

 <span data-ttu-id="fcca3-105">下表顯示語言類型常數，表示可識別程式設計語言的 Guid。</span><span class="sxs-lookup"><span data-stu-id="fcca3-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="fcca3-106">符號</span><span class="sxs-lookup"><span data-stu-id="fcca3-106">Symbol</span></span>|<span data-ttu-id="fcca3-107">描述</span><span class="sxs-lookup"><span data-stu-id="fcca3-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fcca3-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="fcca3-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="fcca3-109">表示 C 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="fcca3-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="fcca3-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="fcca3-111">指出 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="fcca3-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="fcca3-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="fcca3-113">表示 c # 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="fcca3-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="fcca3-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="fcca3-115">表示基礎語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="fcca3-116">CorSym_LanguageType_JAVA</span><span class="sxs-lookup"><span data-stu-id="fcca3-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="fcca3-117">表示 JAVA 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="fcca3-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="fcca3-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="fcca3-119">表示 COBOL 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="fcca3-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="fcca3-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="fcca3-121">表示 Pascal 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="fcca3-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="fcca3-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="fcca3-123">指出 Microsoft 中繼語言 (MSIL) 元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcca3-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="fcca3-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="fcca3-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="fcca3-125">指出 JScript 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="fcca3-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="fcca3-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="fcca3-127">指出 SMC 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="fcca3-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="fcca3-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="fcca3-129">指出針對 .NET Framework 啟用的 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="fcca3-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="fcca3-130">語言廠商常數</span><span class="sxs-lookup"><span data-stu-id="fcca3-130">Language Vendor Constants</span></span>  

 <span data-ttu-id="fcca3-131">下表顯示語言廠商常數，表示可識別程式設計語言廠商的 Guid。</span><span class="sxs-lookup"><span data-stu-id="fcca3-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="fcca3-132">符號</span><span class="sxs-lookup"><span data-stu-id="fcca3-132">Symbol</span></span>|<span data-ttu-id="fcca3-133">描述</span><span class="sxs-lookup"><span data-stu-id="fcca3-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fcca3-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcca3-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="fcca3-135">表示 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="fcca3-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="fcca3-136">檔案類型常數</span><span class="sxs-lookup"><span data-stu-id="fcca3-136">Document Type Constants</span></span>  

 <span data-ttu-id="fcca3-137">下表顯示檔案類型常數，表示可識別檔案類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="fcca3-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="fcca3-138">符號</span><span class="sxs-lookup"><span data-stu-id="fcca3-138">Symbol</span></span>|<span data-ttu-id="fcca3-139">描述</span><span class="sxs-lookup"><span data-stu-id="fcca3-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fcca3-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="fcca3-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="fcca3-141">表示文字檔。</span><span class="sxs-lookup"><span data-stu-id="fcca3-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="fcca3-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="fcca3-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="fcca3-143">表示非文字檔。</span><span class="sxs-lookup"><span data-stu-id="fcca3-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcca3-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcca3-144">See also</span></span>

- [<span data-ttu-id="fcca3-145">非受控 API 參考</span><span class="sxs-lookup"><span data-stu-id="fcca3-145">Unmanaged API Reference</span></span>](index.md)
