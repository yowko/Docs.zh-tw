---
title: 如何：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150567"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="2f6d7-102">如何：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="2f6d7-102">How to: Define the Connection String</span></span>

<span data-ttu-id="2f6d7-103">本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="2f6d7-104">本主題基於[AdventureWorks 銷售](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念模型。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="2f6d7-105">AdventureWorks 銷售模型用於實體框架文檔中與任務相關的主題。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="2f6d7-106">本主題假定您已配置實體框架並定義了 AdventureWorks 銷售模型。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2f6d7-107">有關詳細資訊，請參閱[如何：手動定義模型和映射檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="2f6d7-108">本主題中的過程也包含在["如何：手動設定實體框架專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))"中。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="2f6d7-109">如果在 Visual Studio 專案中使用實體資料模型嚮導，它會自動生成 .edmx 檔並將專案配置為使用實體框架。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="2f6d7-110">有關詳細資訊，請參閱[：使用實體資料模型嚮導](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="2f6d7-111">定義 Entity Framework 連接字串</span><span class="sxs-lookup"><span data-stu-id="2f6d7-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="2f6d7-112">開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="2f6d7-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="2f6d7-113">如果專案沒有應用程式佈建檔，則可以通過從 **"專案**"功能表中選擇 **"添加新專案**"、選擇 **"常規**類別"、"選擇**應用程式佈建檔**"以及按一下"**添加**"來添加一個設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f6d7-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f6d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6d7-114">See also</span></span>

- <span data-ttu-id="2f6d7-115">[快速入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f6d7-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="2f6d7-116">[HOW TO：建立新 .edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f6d7-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="2f6d7-117">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f6d7-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
