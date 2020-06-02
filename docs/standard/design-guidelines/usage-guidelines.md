---
title: 使用指導方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291340"
---
# <a name="usage-guidelines"></a><span data-ttu-id="acae6-102">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="acae6-102">Usage guidelines</span></span>

<span data-ttu-id="acae6-103">本節包含在可公開存取的 Api 中使用一般類型的指導方針。</span><span class="sxs-lookup"><span data-stu-id="acae6-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="acae6-104">它會處理內建架構型別（例如序列化屬性）和多載一般運算子的直接使用。</span><span class="sxs-lookup"><span data-stu-id="acae6-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="acae6-105">本節 <xref:System.IDisposable?displayProperty=nameWithType> 未涵蓋介面，但會在[Dispose 模式](../garbage-collection/implementing-dispose.md)一節中討論。</span><span class="sxs-lookup"><span data-stu-id="acae6-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="acae6-106">如需其他常見內建 .NET Framework 類型的指導方針和其他資訊，請參閱下列的參考主題： <xref:System.DateTime?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset?displayProperty=nameWithType> 、 <xref:System.ICloneable?displayProperty=nameWithType> 、 <xref:System.IComparable%601?displayProperty=nameWithType> 、、、 <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> 、 <xref:System.Uri?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="acae6-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="acae6-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="acae6-107">In this section</span></span>

[<span data-ttu-id="acae6-108">陣列</span><span class="sxs-lookup"><span data-stu-id="acae6-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="acae6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="acae6-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="acae6-110">集合</span><span class="sxs-lookup"><span data-stu-id="acae6-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="acae6-111">序列化</span><span class="sxs-lookup"><span data-stu-id="acae6-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="acae6-112">System.object 使用方式</span><span class="sxs-lookup"><span data-stu-id="acae6-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="acae6-113">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="acae6-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="acae6-114">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="acae6-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="acae6-115">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="acae6-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="acae6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acae6-116">See also</span></span>

- [<span data-ttu-id="acae6-117">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="acae6-117">Framework Design Guidelines</span></span>](index.md)
