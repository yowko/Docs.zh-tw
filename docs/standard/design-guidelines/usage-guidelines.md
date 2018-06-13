---
title: 用法方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02905c193387f78430ce1885449055060d07bf82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571029"
---
# <a name="usage-guidelines"></a><span data-ttu-id="fa502-102">用法方針</span><span class="sxs-lookup"><span data-stu-id="fa502-102">Usage Guidelines</span></span>
<span data-ttu-id="fa502-103">本章節包含使用一般類型，可公開存取的 Api 中的指導方針。</span><span class="sxs-lookup"><span data-stu-id="fa502-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="fa502-104">它說明如何直接使用內建架構類型 （例如序列化屬性） 和一般運算子多載。</span><span class="sxs-lookup"><span data-stu-id="fa502-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="fa502-105"><xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但在討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="fa502-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa502-106">指導方針和其他常見的相關其他相關資訊，如內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fa502-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa502-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa502-107">In This Section</span></span>  
 [<span data-ttu-id="fa502-108">陣列</span><span class="sxs-lookup"><span data-stu-id="fa502-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="fa502-109">屬性</span><span class="sxs-lookup"><span data-stu-id="fa502-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="fa502-110">集合</span><span class="sxs-lookup"><span data-stu-id="fa502-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="fa502-111">序列化</span><span class="sxs-lookup"><span data-stu-id="fa502-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="fa502-112">System.Xml 使用方式</span><span class="sxs-lookup"><span data-stu-id="fa502-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="fa502-113">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="fa502-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="fa502-114">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fa502-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fa502-115">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="fa502-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa502-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa502-116">See Also</span></span>  
 [<span data-ttu-id="fa502-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="fa502-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
