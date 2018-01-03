---
title: "如何：驗證 DBML 和外部對應檔"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9339176cbc6a72d940e3fa053c0e54e0667193f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="f57da-102">如何：驗證 DBML 和外部對應檔</span><span class="sxs-lookup"><span data-stu-id="f57da-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="f57da-103">如果修改外部對應檔案和 .dbml 檔案，則必須根據它們各自的結構描述定義進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f57da-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="f57da-104">這個主題提供實作驗證流程的步驟，供 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 使用者使用。</span><span class="sxs-lookup"><span data-stu-id="f57da-104">This topic provides [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="f57da-105">若要驗證 .dbml 或 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="f57da-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="f57da-106">在 Visual Studio**檔案**功能表上，指向**開啟**，然後按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="f57da-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="f57da-107">在**開啟檔案**對話方塊方塊中，按一下.dbml 或您想要驗證的 XML 對應檔案。</span><span class="sxs-lookup"><span data-stu-id="f57da-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="f57da-108">該檔案中開啟**XML 編輯器**。</span><span class="sxs-lookup"><span data-stu-id="f57da-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="f57da-109">視窗中，以滑鼠右鍵按一下，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="f57da-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f57da-110">在**屬性**視窗中，按一下省略符號**結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="f57da-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="f57da-111">**XML 結構描述**對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f57da-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="f57da-112">請記下適用於您目的的適當結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="f57da-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="f57da-113">DbmlSchema.xsd 是用來驗證 .dbml 檔案的結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="f57da-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="f57da-114">如需詳細資訊，請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f57da-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="f57da-115">LinqToSqlMapping.xsd 是用來驗證外部 XML 對應檔案的結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="f57da-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="f57da-116">如需詳細資訊，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="f57da-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="f57da-117">在**使用**所要結構描述定義資料列，按一下以開啟下拉式清單方塊中，然後按一下 資料行**使用此結構描述**。</span><span class="sxs-lookup"><span data-stu-id="f57da-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="f57da-118">結構描述定義檔案現在已經與 DBML 或 XML 對應檔案產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f57da-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="f57da-119">請確定未選取其他結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="f57da-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="f57da-120">在**檢視**功能表上，按一下 **錯誤清單**。</span><span class="sxs-lookup"><span data-stu-id="f57da-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="f57da-121">判斷是否已產生錯誤、警告或訊息。</span><span class="sxs-lookup"><span data-stu-id="f57da-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="f57da-122">如果未產生，則會根據結構描述定義驗證 XML 檔案為有效。</span><span class="sxs-lookup"><span data-stu-id="f57da-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="f57da-123">提供結構描述定義的替代方法</span><span class="sxs-lookup"><span data-stu-id="f57da-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="f57da-124">如果基於某些原因適用的.xsd 檔案未出現在**XML 結構描述**對話方塊中，您可以從 [說明] 主題中下載.xsd 檔案。</span><span class="sxs-lookup"><span data-stu-id="f57da-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="f57da-125">下列步驟可幫助您以 Unicode 格式儲存下載的檔案，而這種格式是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML 編輯器需要的格式。</span><span class="sxs-lookup"><span data-stu-id="f57da-125">The following steps help you save the downloaded file in the Unicode format required by the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="f57da-126">若要從說明主題中複製結構描述定義檔案</span><span class="sxs-lookup"><span data-stu-id="f57da-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="f57da-127">如這個主題前面所述，找到內含結構描述定義的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="f57da-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="f57da-128">.Dbml 檔案，請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f57da-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="f57da-129">對於外部對應檔案，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="f57da-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="f57da-130">按一下**複製程式碼**將程式碼檔案複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f57da-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="f57da-131">啟動 [記事本]，建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="f57da-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="f57da-132">將剪貼簿中的程式碼貼入 [記事本] 檔案中。</span><span class="sxs-lookup"><span data-stu-id="f57da-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="f57da-133">在 記事本**檔案**功能表上，按一下 **存**。</span><span class="sxs-lookup"><span data-stu-id="f57da-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="f57da-134">在**編碼**方塊中，選取**Unicode**。</span><span class="sxs-lookup"><span data-stu-id="f57da-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f57da-135">這個選項可確保會在文字檔前面加上 Unicode 16 位元組順序標記 (`FFFE`)。</span><span class="sxs-lookup"><span data-stu-id="f57da-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="f57da-136">在**檔案名稱**方塊中，建立副檔名為.xsd 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f57da-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57da-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="f57da-137">See Also</span></span>  
 [<span data-ttu-id="f57da-138">參考資料</span><span class="sxs-lookup"><span data-stu-id="f57da-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
