---
title: "型別提供者疑難排解"
description: "探索可能的解決方案，當您使用 F # 中的型別提供者時遇到最常見的問題。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 44533045-9862-43c5-81d9-3e05157e975a
ms.openlocfilehash: 2b54454d7950dfdd6512d849fd739f505ef3317d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-type-providers"></a><span data-ttu-id="0063e-104">型別提供者疑難排解</span><span class="sxs-lookup"><span data-stu-id="0063e-104">Troubleshooting Type Providers</span></span>

<span data-ttu-id="0063e-105">本主題描述，並提供可能的解決方案會使用型別提供者時遇到最常見的問題。</span><span class="sxs-lookup"><span data-stu-id="0063e-105">This topic describes and provides potential solutions for the problems that you are most likely to encounter when you use type providers.</span></span>


## <a name="possible-problems-with-type-providers"></a><span data-ttu-id="0063e-106">可能發生問題的型別提供者</span><span class="sxs-lookup"><span data-stu-id="0063e-106">Possible Problems with Type Providers</span></span>
<span data-ttu-id="0063e-107">如果您遇到問題，當您使用型別提供者時，您可以檢閱下表針對最常見的解決方案。</span><span class="sxs-lookup"><span data-stu-id="0063e-107">If you encounter a problem when you work with type providers, you can review the following table for the most common solutions.</span></span>



|<span data-ttu-id="0063e-108">問題</span><span class="sxs-lookup"><span data-stu-id="0063e-108">Problem</span></span>|<span data-ttu-id="0063e-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0063e-109">Suggested Actions</span></span>|
|-------|-----------------|
|<span data-ttu-id="0063e-110">**結構描述變更**。</span><span class="sxs-lookup"><span data-stu-id="0063e-110">**Schema Changes**.</span></span> <span data-ttu-id="0063e-111">最適合的資料來源結構描述的型別提供者工作很穩定。</span><span class="sxs-lookup"><span data-stu-id="0063e-111">Type providers work best  when the data source schema is stable.</span></span> <span data-ttu-id="0063e-112">如果您新增資料表或資料行，或對該結構描述進行其他變更，型別提供者無法自動辨識這些變更。</span><span class="sxs-lookup"><span data-stu-id="0063e-112">If you add a data table or column or make another change to that schema, the type provider doesn’t automatically recognize these changes.</span></span>|<span data-ttu-id="0063e-113">清除或重建專案。</span><span class="sxs-lookup"><span data-stu-id="0063e-113">Clean or rebuild the project.</span></span> <span data-ttu-id="0063e-114">若要清除專案，選擇 **建置**，**清除** *ProjectName*功能表列上。</span><span class="sxs-lookup"><span data-stu-id="0063e-114">To clean the project, choose **Build**, **Clean** *ProjectName* on the menu bar.</span></span> <span data-ttu-id="0063e-115">若要重建專案，選擇 **建置**，**重建** *ProjectName*功能表列上。</span><span class="sxs-lookup"><span data-stu-id="0063e-115">To rebuild the project, choose **Build**, **Rebuild** *ProjectName* on the menu bar.</span></span> <span data-ttu-id="0063e-116">這些動作會重設所有型別提供者的狀態，並強制重新連線至資料來源，並取得更新的結構描述資訊提供者。</span><span class="sxs-lookup"><span data-stu-id="0063e-116">These actions reset all type provider state and force the provider to reconnect to the data source and obtain updated schema information.</span></span>|
|<span data-ttu-id="0063e-117">**連線失敗**。</span><span class="sxs-lookup"><span data-stu-id="0063e-117">**Connection Failure**.</span></span> <span data-ttu-id="0063e-118">不正確的 URL 或連接字串、 網路已關閉，或資料來源或服務無法使用。</span><span class="sxs-lookup"><span data-stu-id="0063e-118">The URL or connection string is incorrect, the network is down, or the data source or service is unavailable.</span></span>|<span data-ttu-id="0063e-119">Web 服務或 OData 服務，您可以嘗試驗證 URL 是否正確，且該服務的 Internet Explorer 中的 URL。</span><span class="sxs-lookup"><span data-stu-id="0063e-119">For a web service or OData service, you can try the URL in Internet Explorer to verify whether the URL is correct and the service is available.</span></span> <span data-ttu-id="0063e-120">資料庫連接字串，您可以使用中的資料連接工具**伺服器總管**驗證是否連接字串無效，而且資料庫可供使用。</span><span class="sxs-lookup"><span data-stu-id="0063e-120">For a database connection string, you can use the data connection tools in **Server Explorer** to verify whether the connection string is valid and the database is available.</span></span> <span data-ttu-id="0063e-121">還原您的連線之後，您應該也要清除或重建專案，讓型別提供者會重新連線到網路。</span><span class="sxs-lookup"><span data-stu-id="0063e-121">After you restore your connection, you should then clean or rebuild the project so that the type provider will reconnect to the network.</span></span>|
|<span data-ttu-id="0063e-122">**不是有效的認證**。</span><span class="sxs-lookup"><span data-stu-id="0063e-122">**Not Valid Credentials**.</span></span> <span data-ttu-id="0063e-123">您必須擁有資料來源或 web 服務的有效權限。</span><span class="sxs-lookup"><span data-stu-id="0063e-123">You must have valid permissions for the data source or web service.</span></span>|<span data-ttu-id="0063e-124">SQL 連接，使用者名稱和連接字串或組態檔中指定的密碼必須是有效的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0063e-124">For a SQL connection, the username and the password that are specified in the connection string or configuration file must be valid for the database.</span></span> <span data-ttu-id="0063e-125">如果您使用 Windows 驗證，您必須具有資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="0063e-125">If you are using Windows Authentication, you must have access to the database.</span></span> <span data-ttu-id="0063e-126">資料庫管理員可以識別所需的權限存取每個資料庫和資料庫內的每個項目。</span><span class="sxs-lookup"><span data-stu-id="0063e-126">The database administrator can identify what permissions you need for access to each database and each element within a database.</span></span><br /><br /><span data-ttu-id="0063e-127">Web 服務或資料服務，您必須具有適當認證。</span><span class="sxs-lookup"><span data-stu-id="0063e-127">For a web service or a data service, you must have appropriate credentials.</span></span> <span data-ttu-id="0063e-128">大部分的型別提供者提供 DataContext 物件，其中包含您可以設定為適當的使用者名稱和存取金鑰的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="0063e-128">Most type providers provide a DataContext object, which contains a Credentials property that you can set with the appropriate username and access key.</span></span>|
|<span data-ttu-id="0063e-129">**不是有效的路徑**。</span><span class="sxs-lookup"><span data-stu-id="0063e-129">**Not Valid Path**.</span></span> <span data-ttu-id="0063e-130">檔案的路徑無效。</span><span class="sxs-lookup"><span data-stu-id="0063e-130">A path to a file was not valid.</span></span>|<span data-ttu-id="0063e-131">請確認路徑是否正確，且檔案存在。</span><span class="sxs-lookup"><span data-stu-id="0063e-131">Verify whether the path is correct and the file exists.</span></span> <span data-ttu-id="0063e-132">此外，您必須加上引號的路徑中任何 backlashes 正確，或使用逐字字串或三重括住的字串。</span><span class="sxs-lookup"><span data-stu-id="0063e-132">In addition, you must either quote any backlashes in the path appropriately or use a verbatim string or triple-quoted string.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0063e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0063e-133">See Also</span></span>
[<span data-ttu-id="0063e-134">類型提供者</span><span class="sxs-lookup"><span data-stu-id="0063e-134">Type Providers</span></span>](index.md)
