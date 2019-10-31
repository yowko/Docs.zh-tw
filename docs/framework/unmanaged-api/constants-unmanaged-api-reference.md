---
title: 常數 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
ms.openlocfilehash: 88dfdfcaee4a53e9b3c6e4b7e8187c8bfd5eaa13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099622"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="33f8b-102">常數 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="33f8b-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="33f8b-103">本主題說明在 CorSym 中定義的語言類型、語言廠商和檔案類型常數。</span><span class="sxs-lookup"><span data-stu-id="33f8b-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="33f8b-104">語言類型常數</span><span class="sxs-lookup"><span data-stu-id="33f8b-104">Language Type Constants</span></span>  
 <span data-ttu-id="33f8b-105">下表顯示語言類型常數，代表可識別程式設計語言的 Guid。</span><span class="sxs-lookup"><span data-stu-id="33f8b-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="33f8b-106">符號</span><span class="sxs-lookup"><span data-stu-id="33f8b-106">Symbol</span></span>|<span data-ttu-id="33f8b-107">描述</span><span class="sxs-lookup"><span data-stu-id="33f8b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33f8b-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="33f8b-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="33f8b-109">表示 C 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="33f8b-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="33f8b-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="33f8b-111">表示C++語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="33f8b-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="33f8b-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="33f8b-113">表示C#語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="33f8b-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="33f8b-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="33f8b-115">表示基礎語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="33f8b-116">CorSym_LanguageType_JAVA</span><span class="sxs-lookup"><span data-stu-id="33f8b-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="33f8b-117">表示 JAVA 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="33f8b-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="33f8b-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="33f8b-119">表示 COBOL 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="33f8b-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="33f8b-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="33f8b-121">表示 Pascal 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="33f8b-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="33f8b-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="33f8b-123">表示 Microsoft 中繼語言（MSIL）元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="33f8b-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="33f8b-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="33f8b-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="33f8b-125">表示 JScript 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="33f8b-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="33f8b-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="33f8b-127">表示 SMC 語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="33f8b-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="33f8b-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="33f8b-129">表示 .NET Framework C++啟用的語言。</span><span class="sxs-lookup"><span data-stu-id="33f8b-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="33f8b-130">語言廠商常數</span><span class="sxs-lookup"><span data-stu-id="33f8b-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="33f8b-131">下表顯示語言廠商常數，其代表可識別程式設計語言廠商的 Guid。</span><span class="sxs-lookup"><span data-stu-id="33f8b-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="33f8b-132">符號</span><span class="sxs-lookup"><span data-stu-id="33f8b-132">Symbol</span></span>|<span data-ttu-id="33f8b-133">描述</span><span class="sxs-lookup"><span data-stu-id="33f8b-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33f8b-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="33f8b-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="33f8b-135">表示 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="33f8b-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="33f8b-136">檔案類型常數</span><span class="sxs-lookup"><span data-stu-id="33f8b-136">Document Type Constants</span></span>  
 <span data-ttu-id="33f8b-137">下表顯示檔案類型常數，代表可識別檔案類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="33f8b-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="33f8b-138">符號</span><span class="sxs-lookup"><span data-stu-id="33f8b-138">Symbol</span></span>|<span data-ttu-id="33f8b-139">描述</span><span class="sxs-lookup"><span data-stu-id="33f8b-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33f8b-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="33f8b-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="33f8b-141">表示文字檔。</span><span class="sxs-lookup"><span data-stu-id="33f8b-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="33f8b-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="33f8b-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="33f8b-143">表示非文字檔。</span><span class="sxs-lookup"><span data-stu-id="33f8b-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33f8b-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="33f8b-144">See also</span></span>

- [<span data-ttu-id="33f8b-145">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="33f8b-145">Unmanaged API Reference</span></span>](index.md)
