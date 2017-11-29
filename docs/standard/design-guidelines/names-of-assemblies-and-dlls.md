---
title: "組件和 DLL 的名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 071ca1547898b80440e86df0e4cb9c0667e462ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="19fc0-102">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="19fc0-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="19fc0-103">組件是部署和 managed 程式碼程式的身分識別的單位。</span><span class="sxs-lookup"><span data-stu-id="19fc0-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="19fc0-104">雖然組件可以跨一個或多個檔案，通常是組件以一對一對應的 DLL。</span><span class="sxs-lookup"><span data-stu-id="19fc0-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="19fc0-105">因此，本節會說明只 DLL 命名慣例，然後可以對應至組件命名慣例。</span><span class="sxs-lookup"><span data-stu-id="19fc0-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="19fc0-106">**✓ 不要**選擇的組件提供建議的功能，例如 System.Data 大型區塊的 Dll 名稱。</span><span class="sxs-lookup"><span data-stu-id="19fc0-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="19fc0-107">組件和 DLL 名稱沒有對應至命名空間名稱，但是很合理命名組件時所應遵循的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="19fc0-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="19fc0-108">最佳經驗法則是名稱的組件中所包含的組件的一般前置詞為基礎的 DLL。</span><span class="sxs-lookup"><span data-stu-id="19fc0-108">A good rule of thumb is to name the DLL based on the common prefix of the assemblies contained in the assembly.</span></span> <span data-ttu-id="19fc0-109">例如，兩個命名空間，與組件`MyCompany.MyTechnology.FirstFeature`和`MyCompany.MyTechnology.SecondFeature`，無法呼叫`MyCompany.MyTechnology.dll`。</span><span class="sxs-lookup"><span data-stu-id="19fc0-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="19fc0-110">**✓ 考慮**命名 Dll 根據下列模式：</span><span class="sxs-lookup"><span data-stu-id="19fc0-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="19fc0-111">其中`<Component>`包含一或多個點分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="19fc0-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="19fc0-112">例如: </span><span class="sxs-lookup"><span data-stu-id="19fc0-112">For example:</span></span>  
  
 <span data-ttu-id="19fc0-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="19fc0-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="19fc0-114">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="19fc0-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="19fc0-115">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="19fc0-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fc0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19fc0-116">See Also</span></span>  
 [<span data-ttu-id="19fc0-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="19fc0-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="19fc0-118">命名方針</span><span class="sxs-lookup"><span data-stu-id="19fc0-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
