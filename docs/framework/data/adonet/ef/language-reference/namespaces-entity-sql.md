---
title: 命名空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 395ffb23859be27b4897dfc352f6e44d52286b26
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249987"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="a29f0-102">命名空間 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a29f0-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a29f0-103">導入了命名空間來避免全域識別碼的名稱衝突，例如型別名稱、實體集、函式等等。</span><span class="sxs-lookup"><span data-stu-id="a29f0-103">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="a29f0-104">中[!INCLUDE[esql](../../../../../../includes/esql-md.md)]的命名空間支援類似于 .NET Framework 中的命名空間支援。</span><span class="sxs-lookup"><span data-stu-id="a29f0-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a29f0-105">提供了兩種形式的 USING 子句：限定的命名空間 (為命名空間提供較短的別名) 及不限定的命名空間，如下列範例所述：</span><span class="sxs-lookup"><span data-stu-id="a29f0-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="a29f0-106">名稱解析規則</span><span class="sxs-lookup"><span data-stu-id="a29f0-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="a29f0-107">如果無法在本機範圍中解析識別碼, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]會嘗試在全域範圍 (命名空間) 中尋找名稱。</span><span class="sxs-lookup"><span data-stu-id="a29f0-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a29f0-108">會先嘗試將此識別項 (前置詞) 與其中一個限定的命名空間比對。</span><span class="sxs-lookup"><span data-stu-id="a29f0-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="a29f0-109">如果有相符的結果, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]會嘗試解析指定命名空間中的其餘識別碼。</span><span class="sxs-lookup"><span data-stu-id="a29f0-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="a29f0-110">如果兩者不相符，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a29f0-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="a29f0-111">接下來[!INCLUDE[esql](../../../../../../includes/esql-md.md)] , 嘗試搜尋識別碼的所有未限定命名空間 (在初構中指定)。</span><span class="sxs-lookup"><span data-stu-id="a29f0-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="a29f0-112">如果可以在剛好一個命名空間內找到此識別項，就會傳回該位置。</span><span class="sxs-lookup"><span data-stu-id="a29f0-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="a29f0-113">如果有一個以上的命名空間符合該識別項，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a29f0-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="a29f0-114">如果找不到識別碼的命名空間, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]會將名稱傳遞至下一個外部範圍<xref:System.Data.Common.DbCommand> (或<xref:System.Data.Common.DbConnection>物件), 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="a29f0-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="a29f0-115">與 .NET Framework 的差異</span><span class="sxs-lookup"><span data-stu-id="a29f0-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="a29f0-116">在 .NET Framework 中, 您可以使用部分限定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a29f0-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a29f0-117">則不允許。</span><span class="sxs-lookup"><span data-stu-id="a29f0-117">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="a29f0-118">ADO.NET 使用方式</span><span class="sxs-lookup"><span data-stu-id="a29f0-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="a29f0-119">查詢是透過 ADO.NET <xref:System.Data.Common.DbCommand> 物件來表示。</span><span class="sxs-lookup"><span data-stu-id="a29f0-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="a29f0-120"><xref:System.Data.Common.DbCommand> 物件則可經由 <xref:System.Data.Common.DbConnection> 物件建置。</span><span class="sxs-lookup"><span data-stu-id="a29f0-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="a29f0-121">此外，命名空間也可以指定成 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbConnection> 物件的一部分。</span><span class="sxs-lookup"><span data-stu-id="a29f0-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="a29f0-122">如果[!INCLUDE[esql](../../../../../../includes/esql-md.md)]無法解析查詢本身內的識別碼, 則會探查外部命名空間 (根據類似的規則)。</span><span class="sxs-lookup"><span data-stu-id="a29f0-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29f0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a29f0-123">See also</span></span>

- [<span data-ttu-id="a29f0-124">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="a29f0-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a29f0-125">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="a29f0-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
