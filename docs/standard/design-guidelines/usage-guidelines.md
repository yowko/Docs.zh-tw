---
title: 使用指導方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155401"
---
# <a name="usage-guidelines"></a><span data-ttu-id="4a5b8-102">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="4a5b8-102">Usage guidelines</span></span>

<span data-ttu-id="4a5b8-103">本章節包含使用可公開存取的 Api 中的常見類型的指導方針。</span><span class="sxs-lookup"><span data-stu-id="4a5b8-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="4a5b8-104">它處理的內建的 Framework 類型 （例如，序列化的屬性） 和常見的運算子多載化方式使用。</span><span class="sxs-lookup"><span data-stu-id="4a5b8-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="4a5b8-105"><xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但會討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)一節。</span><span class="sxs-lookup"><span data-stu-id="4a5b8-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="4a5b8-106">如需指導方針和其他常見的其他資訊，內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a5b8-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4a5b8-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="4a5b8-107">In this section</span></span>

[<span data-ttu-id="4a5b8-108">陣列</span><span class="sxs-lookup"><span data-stu-id="4a5b8-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="4a5b8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4a5b8-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="4a5b8-110">集合</span><span class="sxs-lookup"><span data-stu-id="4a5b8-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="4a5b8-111">序列化</span><span class="sxs-lookup"><span data-stu-id="4a5b8-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="4a5b8-112">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="4a5b8-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="4a5b8-113">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="4a5b8-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="4a5b8-114">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="4a5b8-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="4a5b8-115">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="4a5b8-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4a5b8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a5b8-116">See also</span></span>

- [<span data-ttu-id="4a5b8-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4a5b8-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
