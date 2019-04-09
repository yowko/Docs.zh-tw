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
ms.openlocfilehash: 8c76db644ffee478003d834460c155c4ec6d0070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133948"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="026db-102">常數 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="026db-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="026db-103">本主題描述的語言類型、 語言廠商和定義於 CorSym.idl 中的文件類型常數。</span><span class="sxs-lookup"><span data-stu-id="026db-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="026db-104">語言類型常數</span><span class="sxs-lookup"><span data-stu-id="026db-104">Language Type Constants</span></span>  
 <span data-ttu-id="026db-105">下表顯示的語言類型的常數，表示識別程式設計語言的 Guid。</span><span class="sxs-lookup"><span data-stu-id="026db-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="026db-106">符號</span><span class="sxs-lookup"><span data-stu-id="026db-106">Symbol</span></span>|<span data-ttu-id="026db-107">描述</span><span class="sxs-lookup"><span data-stu-id="026db-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="026db-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="026db-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="026db-109">表示 C 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="026db-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="026db-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="026db-111">表示 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="026db-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="026db-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="026db-113">表示C#語言。</span><span class="sxs-lookup"><span data-stu-id="026db-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="026db-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="026db-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="026db-115">表示基本的語言。</span><span class="sxs-lookup"><span data-stu-id="026db-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="026db-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="026db-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="026db-117">表示 Java 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="026db-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="026db-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="026db-119">表示的 COBOL 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="026db-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="026db-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="026db-121">表示的 Pascal 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="026db-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="026db-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="026db-123">表示 Microsoft intermediate language (MSIL) 組件程式碼。</span><span class="sxs-lookup"><span data-stu-id="026db-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="026db-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="026db-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="026db-125">表示 JScript 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="026db-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="026db-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="026db-127">表示的 SMC 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="026db-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="026db-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="026db-129">表示啟用.NET framework 的 c + + 語言。</span><span class="sxs-lookup"><span data-stu-id="026db-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="026db-130">語言廠商常數</span><span class="sxs-lookup"><span data-stu-id="026db-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="026db-131">下表顯示的語言廠商的常數，表示識別程式設計語言廠商的 Guid。</span><span class="sxs-lookup"><span data-stu-id="026db-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="026db-132">符號</span><span class="sxs-lookup"><span data-stu-id="026db-132">Symbol</span></span>|<span data-ttu-id="026db-133">描述</span><span class="sxs-lookup"><span data-stu-id="026db-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="026db-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="026db-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="026db-135">表示 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="026db-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="026db-136">文件類型常數</span><span class="sxs-lookup"><span data-stu-id="026db-136">Document Type Constants</span></span>  
 <span data-ttu-id="026db-137">下表顯示文件類型的常數，表示識別文件類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="026db-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="026db-138">符號</span><span class="sxs-lookup"><span data-stu-id="026db-138">Symbol</span></span>|<span data-ttu-id="026db-139">描述</span><span class="sxs-lookup"><span data-stu-id="026db-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="026db-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="026db-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="026db-141">表示文字文件。</span><span class="sxs-lookup"><span data-stu-id="026db-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="026db-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="026db-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="026db-143">表示非文字文件。</span><span class="sxs-lookup"><span data-stu-id="026db-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="026db-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="026db-144">See also</span></span>

- [<span data-ttu-id="026db-145">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="026db-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
