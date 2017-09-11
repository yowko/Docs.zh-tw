---
title: "範例 XML 文件 (LINQ to XML) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a734cc4e-d95d-4631-91a2-81618c8ad894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: df50a49831031edaa1ac349efa9a5ff9b6688dd8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sample-xml-documents-linq-to-xml"></a><span data-ttu-id="5f1d7-102">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-102">Sample XML Documents (LINQ to XML)</span></span>
<span data-ttu-id="5f1d7-103">下列範例檔案中的程式碼範例和整個程式碼片段使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-103">The following example files are used in the code samples and code snippets throughout the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f1d7-104">此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-104">The example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious.</span></span> <span data-ttu-id="5f1d7-105">並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-105">No association with any real company, organization, product, domain name, e-mail address, logo, person, places, or events is intended or should be inferred.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f1d7-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5f1d7-106">In This Section</span></span>  
  
|<span data-ttu-id="5f1d7-107">主題</span><span class="sxs-lookup"><span data-stu-id="5f1d7-107">Topic</span></span>|<span data-ttu-id="5f1d7-108">描述</span><span class="sxs-lookup"><span data-stu-id="5f1d7-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5f1d7-109">範例 XML 檔：典型採購訂單 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-109">Sample XML File: Typical Purchase Order (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)|<span data-ttu-id="5f1d7-110">包含典型採購訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-110">An XML document that contains a typical purchase order.</span></span>|  
|[<span data-ttu-id="5f1d7-111">範例 XML 檔：命名空間中的典型採購訂單</span><span class="sxs-lookup"><span data-stu-id="5f1d7-111">Sample XML File: Typical Purchase Order in a Namespace</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)|<span data-ttu-id="5f1d7-112">在命名空間中，包含典型採購訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-112">An XML document in a namespace that contains a typical purchase order.</span></span>|  
|[<span data-ttu-id="5f1d7-113">範例 XML 檔：多份採購訂單 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-113">Sample XML File: Multiple Purchase Orders (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)|<span data-ttu-id="5f1d7-114">包含多個採購訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-114">An XML document that contains multiple purchase orders.</span></span>|  
|[<span data-ttu-id="5f1d7-115">範例 XML 檔：命名空間中的多份採購訂單</span><span class="sxs-lookup"><span data-stu-id="5f1d7-115">Sample XML File: Multiple Purchase Orders in a Namespace</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)|<span data-ttu-id="5f1d7-116">在命名空間中，包含多個採購訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-116">An XML document in a namespace that contains multiple purchase orders.</span></span>|  
|[<span data-ttu-id="5f1d7-117">範例 XML 檔：測試組態 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-117">Sample XML File: Test Configuration (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)|<span data-ttu-id="5f1d7-118">包含某些虛擬測試組態資料的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-118">An XML document that contains some pseudo test configuration data.</span></span>|  
|[<span data-ttu-id="5f1d7-119">範例 XML 檔：命名空間中的測試組態</span><span class="sxs-lookup"><span data-stu-id="5f1d7-119">Sample XML File: Test Configuration in a Namespace</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md)|<span data-ttu-id="5f1d7-120">在命名空間中，包含某些虛擬測試組態資料的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-120">An XML document in a namespace that contains some pseudo test configuration data.</span></span>|  
|[<span data-ttu-id="5f1d7-121">範例 XML 檔：客戶和訂單 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-121">Sample XML File: Customers and Orders (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)|<span data-ttu-id="5f1d7-122">包含客戶和訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-122">An XML document that contains customers and orders.</span></span>|  
|[<span data-ttu-id="5f1d7-123">範例 XSD 檔：客戶和訂單</span><span class="sxs-lookup"><span data-stu-id="5f1d7-123">Sample XSD File: Customers and Orders</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)|<span data-ttu-id="5f1d7-124">Xml 結構描述定義 (XSD) 驗證[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](http://msdn.microsoft.com/library/26790c41-5976-4558-a096-d0f67bfc4d92)。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-124">An Xml Schema Definition (XSD) that validates the [Sample XML File: Customers and Orders (LINQ to XML)](http://msdn.microsoft.com/library/26790c41-5976-4558-a096-d0f67bfc4d92).</span></span>|  
|[<span data-ttu-id="5f1d7-125">範例 XML 檔：位於相同命名空間中的客戶和訂單</span><span class="sxs-lookup"><span data-stu-id="5f1d7-125">Sample XML File: Customers and Orders in a Namespace</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md)|<span data-ttu-id="5f1d7-126">在命名空間中，包含客戶和訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-126">An XML document in a namespace that contains customers and orders.</span></span>|  
|[<span data-ttu-id="5f1d7-127">範例 XML 檔：數值資料 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-127">Sample XML File: Numerical Data (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)|<span data-ttu-id="5f1d7-128">包含適合加總與群組之資料的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-128">An XML document that contains data suitable for summing and grouping.</span></span>|  
|[<span data-ttu-id="5f1d7-129">範例 XML 檔：命名空間中的數值資料</span><span class="sxs-lookup"><span data-stu-id="5f1d7-129">Sample XML File: Numerical Data in a Namespace</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)|<span data-ttu-id="5f1d7-130">在命名空間中，包含適合加總與群組之資料的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-130">An XML document in a namespace that contains data suitable for summing and grouping.</span></span>|  
|[<span data-ttu-id="5f1d7-131">範例 XML 檔：書籍 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-131">Sample XML File: Books (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)|<span data-ttu-id="5f1d7-132">包含書籍目錄的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-132">An XML document that contains a catalog of books.</span></span>|  
|[<span data-ttu-id="5f1d7-133">範例 XML 檔：合併的採購訂單</span><span class="sxs-lookup"><span data-stu-id="5f1d7-133">Sample XML File: Consolidated Purchase Orders</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md)|<span data-ttu-id="5f1d7-134">呈現包含不同命名空間中之採購訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-134">Presents an XML document that contains purchase orders that are in different namespaces.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f1d7-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f1d7-135">See Also</span></span>  
 [<span data-ttu-id="5f1d7-136">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f1d7-136">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
