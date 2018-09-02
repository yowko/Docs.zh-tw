---
title: 處理物件
ms.date: 03/30/2017
ms.assetid: 338d8a55-05cc-46b0-bbb8-1379d77068e9
ms.openlocfilehash: ad6288b3b6ceabb419d88da9ff81abec177f55d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424058"
---
# <a name="working-with-objects"></a><span data-ttu-id="8d34b-102">處理物件</span><span class="sxs-lookup"><span data-stu-id="8d34b-102">Working with Objects</span></span>
<span data-ttu-id="8d34b-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 可讓您查詢、插入、更新及刪除資料 (這些資料表示為實體型別執行個體的具型別 Common Language Runtime (CLR) 物件)。</span><span class="sxs-lookup"><span data-stu-id="8d34b-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to query, insert, update, and delete data, which is expressed as typed common language runtime (CLR) objects that are instances of entity types.</span></span> <span data-ttu-id="8d34b-104">這些實體類型代表在概念模型中定義的實體。</span><span class="sxs-lookup"><span data-stu-id="8d34b-104">The entity types represent the entities defined in the conceptual model.</span></span> <span data-ttu-id="8d34b-105">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會將概念模型中定義的實體和關聯性對應至資料來源。</span><span class="sxs-lookup"><span data-stu-id="8d34b-105">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] maps entities and relationships that are defined in a conceptual model to a data source.</span></span> <span data-ttu-id="8d34b-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供的工具可執行下列動作： 具體化為物件資料來源傳回的資料; 追蹤對物件所做的變更; 處理的並行存取; 物件將變更傳播回資料來源，並將物件繫結至控制項。</span><span class="sxs-lookup"><span data-stu-id="8d34b-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provides facilities to do the following: materialize data returned from the data source as objects; track changes that were made to the objects; handle concurrency; propagate object changes back to the data source; and bind objects to controls.</span></span>  
  
 <span data-ttu-id="8d34b-107">如需有關使用最新版的 Entity Framework，請參閱中的物件的詳細資訊[使用物件](https://go.microsoft.com/fwlink/?LinkId=235289)。</span><span class="sxs-lookup"><span data-stu-id="8d34b-107">For more information about working with objects in the latest version of the Entity Framework see, [Working with Objects](https://go.microsoft.com/fwlink/?LinkId=235289).</span></span>
