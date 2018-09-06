---
title: 使用指導方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e44a6b58fd334b6a23e113922b980f69de627b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869862"
---
# <a name="usage-guidelines"></a><span data-ttu-id="b34e0-102">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="b34e0-102">Usage guidelines</span></span>

<span data-ttu-id="b34e0-103">本章節包含使用可公開存取的 Api 中的常見類型的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b34e0-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="b34e0-104">它處理的內建的 Framework 類型 （例如，序列化的屬性） 和常見的運算子多載化方式使用。</span><span class="sxs-lookup"><span data-stu-id="b34e0-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="b34e0-105"><xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但會討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)一節。</span><span class="sxs-lookup"><span data-stu-id="b34e0-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="b34e0-106">如指導方針和其他常見的相關其他相關資訊，內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b34e0-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b34e0-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b34e0-107">In this section</span></span>

[<span data-ttu-id="b34e0-108">陣列</span><span class="sxs-lookup"><span data-stu-id="b34e0-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="b34e0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b34e0-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="b34e0-110">集合</span><span class="sxs-lookup"><span data-stu-id="b34e0-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="b34e0-111">序列化</span><span class="sxs-lookup"><span data-stu-id="b34e0-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="b34e0-112">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="b34e0-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="b34e0-113">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="b34e0-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="b34e0-114">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b34e0-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="b34e0-115">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="b34e0-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b34e0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b34e0-116">See also</span></span>

- [<span data-ttu-id="b34e0-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b34e0-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
