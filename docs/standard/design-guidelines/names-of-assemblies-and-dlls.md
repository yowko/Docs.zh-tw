---
title: 組件和 DLL 的名稱
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516431"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="eabff-102">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="eabff-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="eabff-103">組件是部署和 managed 程式碼程式的身分識別的單位。</span><span class="sxs-lookup"><span data-stu-id="eabff-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="eabff-104">雖然組件可以跨越一或多個檔案，通常對應一對一與 DLL 組件。</span><span class="sxs-lookup"><span data-stu-id="eabff-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="eabff-105">因此，本節會描述唯一 DLL 命名慣例，則可以對應至組件命名慣例。</span><span class="sxs-lookup"><span data-stu-id="eabff-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="eabff-106">**✓ DO** 選擇的組件提供建議的功能，例如 System.Data 大型區塊的 Dll 名稱。</span><span class="sxs-lookup"><span data-stu-id="eabff-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="eabff-107">組件和 DLL 的名稱不一定要對應至命名空間名稱，但很合理地命名組件時，請遵循此命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="eabff-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="eabff-108">好的經驗法則是命名為基礎的共同首碼的組件中包含的命名空間的 DLL。</span><span class="sxs-lookup"><span data-stu-id="eabff-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="eabff-109">比方說，有兩個命名空間，組件`MyCompany.MyTechnology.FirstFeature`並`MyCompany.MyTechnology.SecondFeature`，可能會呼叫`MyCompany.MyTechnology.dll`。</span><span class="sxs-lookup"><span data-stu-id="eabff-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="eabff-110">**✓ CONSIDER** 命名 Dll 根據下列模式：</span><span class="sxs-lookup"><span data-stu-id="eabff-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="eabff-111">其中`<Component>`包含一或多個點分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="eabff-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="eabff-112">例如: </span><span class="sxs-lookup"><span data-stu-id="eabff-112">For example:</span></span>  
  
 <span data-ttu-id="eabff-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="eabff-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="eabff-114">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="eabff-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="eabff-115">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="eabff-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabff-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eabff-116">See also</span></span>

- [<span data-ttu-id="eabff-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="eabff-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="eabff-118">命名方針</span><span class="sxs-lookup"><span data-stu-id="eabff-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
