---
title: 作法：手動產生用戶端資料服務類別（WCF Data Services）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 106f1cedb33c0c1b333df0b9f2b8c2a70d458a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790421"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="e1a45-102">HOW TO：手動產生用戶端資料服務類別（WCF Data Services）</span><span class="sxs-lookup"><span data-stu-id="e1a45-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="e1a45-103">WCF Data Services 與 Visual Studio 整合，可讓您在使用 [**加入服務參考**] 對話方塊，將參考加入至 Visual Studio 專案中的資料服務時，自動產生用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="e1a45-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="e1a45-104">如需詳細資訊，請參閱[如何：加入資料服務參考](how-to-add-a-data-service-reference-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a45-104">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="e1a45-105">您也可以使用程式碼產生工具 `DataSvcUtil.exe`，手動產生同樣的用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="e1a45-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="e1a45-106">此工具隨附于 WCF Data Services，會從資料服務定義產生 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="e1a45-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="e1a45-107">同時，這項工具也可根據概念模型 (.csdl) 檔案，以及在 Visual Studio 專案中代表 Entity Framework 模型的 .edmx 檔案產生資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="e1a45-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="e1a45-108">本主題的範例會根據 Northwind 範例資料服務建立用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="e1a45-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="e1a45-109">此服務會在您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。</span><span class="sxs-lookup"><span data-stu-id="e1a45-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="e1a45-110">本主題中的某些範例需要 Northwind 模型的概念模型檔案。</span><span class="sxs-lookup"><span data-stu-id="e1a45-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="e1a45-111">如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生模型和對應](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。</span><span class="sxs-lookup"><span data-stu-id="e1a45-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="e1a45-112">本主題中的某些範例需要 Northwind 模型的 .edmx 檔。</span><span class="sxs-lookup"><span data-stu-id="e1a45-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="e1a45-113">如需詳細資訊，請參閱[.edmx 檔案總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e1a45-113">For more information, see [.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="e1a45-114">產生支援資料繫結的 C# 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="e1a45-115">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="e1a45-116">您必須將提供給 `/uri:` 參數的值改為您的 Northwind 範例資料服務執行個體的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a45-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="e1a45-117">產生支援資料繫結的 Visual Basic 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="e1a45-118">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="e1a45-119">您必須將提供給 `/uri:` 參數的值改為您的 Northwind 資料服務範本之執行個體的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a45-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="e1a45-120">根據服務 URI 產生 C# 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="e1a45-121">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="e1a45-122">您必須將提供給 `/uri:` 參數的值改為您的 Northwind 範例資料服務執行個體的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a45-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="e1a45-123">根據服務 URI 產生 Visual Basic 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="e1a45-124">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="e1a45-125">您必須將提供給 `/uri:` 參數的值改為您的 Northwind 資料服務範本之執行個體的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1a45-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e1a45-126">根據概念模型檔 (CSDL) 產生 C# 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="e1a45-127">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e1a45-128">根據概念模型檔 (CSDL) 產生 Visual Basic 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="e1a45-129">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="e1a45-130">根據 .edmx 檔產生 C# 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="e1a45-131">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="e1a45-132">根據服務 .edmx 檔產生 Visual Basic 類別</span><span class="sxs-lookup"><span data-stu-id="e1a45-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="e1a45-133">在命令提示字元中，執行下列命令但不含分行符號：</span><span class="sxs-lookup"><span data-stu-id="e1a45-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="e1a45-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a45-134">See also</span></span>

- [<span data-ttu-id="e1a45-135">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="e1a45-135">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="e1a45-136">如何：加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="e1a45-136">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="e1a45-137">WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="e1a45-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)
