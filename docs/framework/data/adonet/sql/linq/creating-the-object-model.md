---
title: "建立物件模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb6f8683ce49c8115b6dce477d0e61369d7abeef
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="creating-the-object-model"></a><span data-ttu-id="766c7-102">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="766c7-102">Creating the Object Model</span></span>
<span data-ttu-id="766c7-103">您可以從現有的資料庫建立物件模型 (Object Model)，並且使用預設狀態下的模型。</span><span class="sxs-lookup"><span data-stu-id="766c7-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="766c7-104">您也可以自訂模型的各個層面及其行為。</span><span class="sxs-lookup"><span data-stu-id="766c7-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="766c7-105">如果您使用[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，您可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="766c7-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="766c7-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="766c7-106">In This Section</span></span>  
 [<span data-ttu-id="766c7-107">如何：以 Visual Basic 或 C# 產生物件模型</span><span class="sxs-lookup"><span data-stu-id="766c7-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="766c7-108">說明如何使用 SQLMetal 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="766c7-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="766c7-109">同時也為 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 使用者提供[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]的連結。</span><span class="sxs-lookup"><span data-stu-id="766c7-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users</span></span>  
  
 [<span data-ttu-id="766c7-110">如何：產生物件模型當作外部檔案</span><span class="sxs-lookup"><span data-stu-id="766c7-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="766c7-111">說明如何產生外部對應檔案，而不要使用以屬性 (Attribute) 為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="766c7-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="766c7-112">如何：藉由修改 DBML 檔案產生自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="766c7-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="766c7-113">說明如何從 DBML 中繼資料 (Metadata) 檔產生 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 或 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="766c7-113">Describes how to generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="766c7-114">如何：驗證 DBML 和外部對應檔</span><span class="sxs-lookup"><span data-stu-id="766c7-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="766c7-115">說明如何驗證您已修改的對應檔 (進階)。</span><span class="sxs-lookup"><span data-stu-id="766c7-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="766c7-116">如何：讓實體可序列化</span><span class="sxs-lookup"><span data-stu-id="766c7-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="766c7-117">說明如何加入適當的屬性，讓實體變成可以序列化。</span><span class="sxs-lookup"><span data-stu-id="766c7-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="766c7-118">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="766c7-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="766c7-119">說明如何使用程式碼編輯器來撰寫您自己的對應程式碼，或是自訂已自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="766c7-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="766c7-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="766c7-120">Related Sections</span></span>  
 [<span data-ttu-id="766c7-121">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="766c7-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="766c7-122">提供有關的詳細資料[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]物件模型。</span><span class="sxs-lookup"><span data-stu-id="766c7-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="766c7-123">LINQ to SQL 的典型使用步驟</span><span class="sxs-lookup"><span data-stu-id="766c7-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="766c7-124">說明您實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式時所遵循的典型步驟。</span><span class="sxs-lookup"><span data-stu-id="766c7-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
