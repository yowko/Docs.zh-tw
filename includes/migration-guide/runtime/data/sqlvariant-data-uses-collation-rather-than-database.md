---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235147"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="2931e-101">Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序</span><span class="sxs-lookup"><span data-stu-id="2931e-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2931e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2931e-102">Details</span></span>|<code>sql_variant</code> <span data-ttu-id="2931e-103">資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="2931e-103">data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="2931e-104">建議</span><span class="sxs-lookup"><span data-stu-id="2931e-104">Suggestion</span></span>|<span data-ttu-id="2931e-105">這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。</span><span class="sxs-lookup"><span data-stu-id="2931e-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="2931e-106">依賴損毀資料的應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="2931e-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="2931e-107">範圍</span><span class="sxs-lookup"><span data-stu-id="2931e-107">Scope</span></span>|<span data-ttu-id="2931e-108">透明</span><span class="sxs-lookup"><span data-stu-id="2931e-108">Transparent</span></span>|
|<span data-ttu-id="2931e-109">版本</span><span class="sxs-lookup"><span data-stu-id="2931e-109">Version</span></span>|<span data-ttu-id="2931e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="2931e-110">4.5</span></span>|
|<span data-ttu-id="2931e-111">類型</span><span class="sxs-lookup"><span data-stu-id="2931e-111">Type</span></span>|<span data-ttu-id="2931e-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="2931e-112">Runtime</span></span>|
