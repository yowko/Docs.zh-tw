---
title: 組件和 DLL 的名稱
description: 瞭解 (Dll) 命名元件和動態連結程式庫的指導方針。 元件可以跨越一或多個檔案，但它通常會以一個 DLL 對應到一個或多個檔案。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 2d1484889eb7db537de970c31109f26a6d61ad8d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830047"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="83e7e-104">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="83e7e-104">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="83e7e-105">元件是 managed 程式碼程式的部署和身分識別單位。</span><span class="sxs-lookup"><span data-stu-id="83e7e-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="83e7e-106">雖然元件可以跨越一或多個檔案，但通常元件會以一個 DLL 對應到一個元件。</span><span class="sxs-lookup"><span data-stu-id="83e7e-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="83e7e-107">因此，本節只會說明 DLL 命名慣例，然後可以對應至元件命名慣例。</span><span class="sxs-lookup"><span data-stu-id="83e7e-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="83e7e-108">✔️請選擇您的元件 Dll 名稱，以建議大量的功能，例如 System.object。</span><span class="sxs-lookup"><span data-stu-id="83e7e-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="83e7e-109">元件和 DLL 名稱不一定要對應至命名空間名稱，但在命名元件時，請遵循命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="83e7e-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="83e7e-110">理想的經驗法則是根據元件中包含的命名空間一般前置詞來命名 DLL。</span><span class="sxs-lookup"><span data-stu-id="83e7e-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="83e7e-111">例如，有兩個命名空間和的 `MyCompany.MyTechnology.FirstFeature` 元件 `MyCompany.MyTechnology.SecondFeature` 可以被呼叫 `MyCompany.MyTechnology.dll` 。</span><span class="sxs-lookup"><span data-stu-id="83e7e-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="83e7e-112">✔️考慮根據下列模式來命名 Dll：</span><span class="sxs-lookup"><span data-stu-id="83e7e-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="83e7e-113">其中 `<Component>` 包含一或多個以點分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="83e7e-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="83e7e-114">例如：</span><span class="sxs-lookup"><span data-stu-id="83e7e-114">For example:</span></span>

 <span data-ttu-id="83e7e-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="83e7e-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="83e7e-116">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="83e7e-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="83e7e-117">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="83e7e-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="83e7e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="83e7e-118">See also</span></span>

- [<span data-ttu-id="83e7e-119">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="83e7e-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="83e7e-120">命名指導方針</span><span class="sxs-lookup"><span data-stu-id="83e7e-120">Naming Guidelines</span></span>](naming-guidelines.md)
