---
title: 組件和 DLL 的名稱
description: 瞭解命名元件和動態連結程式庫（Dll）的指導方針。 元件可以跨越一個或多個檔案，但它通常會與 DLL 對應一對一。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: de7ce3ee774d4598521d7156d0d660c3fe30154c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594474"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="430a9-104">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="430a9-104">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="430a9-105">「元件」（assembly）是受控碼程式的部署和身分識別單位。</span><span class="sxs-lookup"><span data-stu-id="430a9-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="430a9-106">雖然元件可以跨越一個或多個檔案，但通常元件會與 DLL 對應一對一。</span><span class="sxs-lookup"><span data-stu-id="430a9-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="430a9-107">因此，本節只會描述 DLL 命名慣例，然後對應至元件命名慣例。</span><span class="sxs-lookup"><span data-stu-id="430a9-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="430a9-108">✔️確實會針對您的元件 Dll 選擇名稱，以建議很大的功能區塊，例如 System.object。</span><span class="sxs-lookup"><span data-stu-id="430a9-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="430a9-109">元件和 DLL 名稱不一定要對應至命名空間名稱，但在命名元件時，可以合理遵循命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="430a9-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="430a9-110">理想的經驗法則是根據元件中所含命名空間的通用前置詞來命名 DLL。</span><span class="sxs-lookup"><span data-stu-id="430a9-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="430a9-111">例如，可以呼叫具有兩個命名空間 `MyCompany.MyTechnology.FirstFeature` 和的元件 `MyCompany.MyTechnology.SecondFeature` `MyCompany.MyTechnology.dll` 。</span><span class="sxs-lookup"><span data-stu-id="430a9-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="430a9-112">✔️考慮根據下列模式來命名 Dll：</span><span class="sxs-lookup"><span data-stu-id="430a9-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="430a9-113">其中 `<Component>` 包含一或多個以點分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="430a9-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="430a9-114">例如：</span><span class="sxs-lookup"><span data-stu-id="430a9-114">For example:</span></span>

 <span data-ttu-id="430a9-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="430a9-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="430a9-116">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="430a9-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="430a9-117">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="430a9-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="430a9-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="430a9-118">See also</span></span>

- [<span data-ttu-id="430a9-119">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="430a9-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="430a9-120">命名方針</span><span class="sxs-lookup"><span data-stu-id="430a9-120">Naming Guidelines</span></span>](naming-guidelines.md)
