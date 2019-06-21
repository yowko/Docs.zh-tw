---
title: 作法：定義連接字串
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 8386f93d0e80aa824b1e91a130812b9b3a2b3619
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306377"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="49bc1-102">作法：定義連接字串</span><span class="sxs-lookup"><span data-stu-id="49bc1-102">How to: Define the Connection String</span></span>

<span data-ttu-id="49bc1-103">本主題將示範如何定義連接至概念模型時所使用的連接字串 (Connection String)。</span><span class="sxs-lookup"><span data-stu-id="49bc1-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="49bc1-104">本主題根據[AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))概念模型。</span><span class="sxs-lookup"><span data-stu-id="49bc1-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="49bc1-105">AdventureWorks Sales Model 會在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 文件的所有工作相關的主題內使用。</span><span class="sxs-lookup"><span data-stu-id="49bc1-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="49bc1-106">本主題假設您已經設定[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]並且定義 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="49bc1-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="49bc1-107">如需詳細資訊，請參閱[如何：手動定義模型和對應檔](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49bc1-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="49bc1-108">本主題中的程序也會包含在[How to:手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="49bc1-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="49bc1-109">如果您在 Visual Studio 專案使用 Entity Data Model 精靈，會自動產生.edmx 檔案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="49bc1-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="49bc1-110">如需詳細資訊，請參閱[如何：使用實體資料模型精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49bc1-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="49bc1-111">定義 Entity Framework 連接字串</span><span class="sxs-lookup"><span data-stu-id="49bc1-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="49bc1-112">開啟專案的應用程式組態檔 (app.config) 並加入下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="49bc1-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="49bc1-113">如果您的專案沒有應用程式組態檔，您可以加入一個方法是選取**加入新項目**從**專案**功能表上，選取**一般**類別選取**應用程式組態檔**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="49bc1-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="49bc1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49bc1-114">See also</span></span>

- <span data-ttu-id="49bc1-115">[快速入門](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49bc1-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="49bc1-116">[如何：建立新.edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49bc1-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="49bc1-117">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49bc1-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
