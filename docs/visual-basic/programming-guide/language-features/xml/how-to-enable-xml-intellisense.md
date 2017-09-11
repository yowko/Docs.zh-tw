---
title: "如何︰ 啟用 XML IntelliSense 在 Visual Basic |Microsoft 文件"
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
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e367016c93586ad34492628b6a4384a5ef1b6acd
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="c5b87-102">如何：啟用 Visual Basic 中的 XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c5b87-102">How to: Enable XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="c5b87-103">在 Visual Basic 中的 XML IntelliSense 提供 XML 結構描述中定義的項目文字的完成。</span><span class="sxs-lookup"><span data-stu-id="c5b87-103">XML IntelliSense in Visual Basic provides word completion for elements that are defined in an XML schema.</span></span> <span data-ttu-id="c5b87-104">若要啟用 XML IntelliSense，Visual Basic 中，您必須執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="c5b87-104">To enable XML IntelliSense in Visual Basic, you must do the following:</span></span>  
  
1.  <span data-ttu-id="c5b87-105">取得 XML 結構描述 (XSD) 檔案或檔案，您的應用程式會讀取或寫入的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-105">Obtain the XML schema (XSD) file or files for the XML files that your application will read from or write to.</span></span>  
  
2.  <span data-ttu-id="c5b87-106">在專案中包含的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-106">Include the XML schema files in your project.</span></span>  
  
3.  <span data-ttu-id="c5b87-107">匯入到您的程式碼檔案或專案的目標命名空間或命名空間。</span><span class="sxs-lookup"><span data-stu-id="c5b87-107">Import the target namespace or namespaces into your code file or project.</span></span> <span data-ttu-id="c5b87-108">目標命名空間由`targetNamespace`或`tns`XSD 結構描述的屬性。</span><span class="sxs-lookup"><span data-stu-id="c5b87-108">A target namespace is identified by the `targetNamespace` or `tns` attribute of your XSD schema.</span></span>  
  
     <span data-ttu-id="c5b87-109">若要匯入目標命名空間，請使用`Imports`陳述式，或將之命名空間的所有程式碼檔案加入專案中，使用**參考**頁面的 專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="c5b87-109">To import a target namespace, use the `Imports` statement, or add a namespace for all code files in a project by using the **References** page of the Project Designer.</span></span>  
  
 <span data-ttu-id="c5b87-110">多個功能在 Visual Basic 中的 XML IntelliSense 的詳細資訊，請參閱[Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-110">For more information on the capabilities of XML IntelliSense in Visual Basic, see [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span></span> <span data-ttu-id="c5b87-111">如需有關匯入 XML 命名空間的詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)或[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-111">For more information on importing XML namespaces, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) or [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="c5b87-112">![視訊連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")如本主題的影片版本，請參閱[影片-如何︰ 在 Visual Basic 中啟用 XML IntelliSense](http://go.microsoft.com/fwlink/?LinkId=102466)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Enable XML IntelliSense in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span></span> <span data-ttu-id="c5b87-113">如需相關的影片示範，請參閱[如何啟用 XML IntelliSense 和使用 XML 命名空間？](http://go.microsoft.com/fwlink/?LinkId=143035)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-113">For a related video demonstration, see [How Do I Enable XML IntelliSense and Use XML Namespaces?](http://go.microsoft.com/fwlink/?LinkId=143035).</span></span>  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="c5b87-114">啟用在 Visual Basic 中的 XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c5b87-114">Enable XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="c5b87-115">如果您有一個 XML 檔案，但它沒有 XSD 結構描述檔案，SP1 中您可以建立 XSD 結構描述檔案使用 XML 結構描述精靈。</span><span class="sxs-lookup"><span data-stu-id="c5b87-115">If you have an XML file but you do not have an XSD schema file for it, in SP1 you can create an XSD schema file by using the XML to Schema Wizard.</span></span> <span data-ttu-id="c5b87-116">您也可以使用結構描述推斷 Visual Studio XML 編輯器。</span><span class="sxs-lookup"><span data-stu-id="c5b87-116">You can also use schema inference in the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a><span data-ttu-id="c5b87-117">若要使用的 XML 結構描述精靈 建立 XSD 結構描述檔案的 XML 檔案 （需要 SP1）</span><span class="sxs-lookup"><span data-stu-id="c5b87-117">To create an XSD schema file for an XML file by using the XML to Schema Wizard (requires SP1)</span></span>  
  
1.  <span data-ttu-id="c5b87-118">在專案中，按一下 **加入新項目**上**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="c5b87-118">In your project, click **Add New Item** on the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="c5b87-119">選取**Xml 結構描述**項目範本，從**資料**或**一般項目**範本類別目錄。</span><span class="sxs-lookup"><span data-stu-id="c5b87-119">Select the **Xml to Schema** item template from either the **Data** or **Common Items** template categories.</span></span>  
  
3.  <span data-ttu-id="c5b87-120">提供 XSD 檔案或檔案，推斷的結構描述集合會儲存在然後按一下 檔案名稱**新增**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-120">Provide a file name for the XSD file or files that the inferred schema set will be stored in, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="c5b87-121">在**推斷 XML 結構描述集從 XML 文件** 視窗中，新增一或多個 XML 文件推斷 XML 結構描述集。</span><span class="sxs-lookup"><span data-stu-id="c5b87-121">In the **Infer XML Schema set from XML documents** window, add one or more XML documents to infer the XML schema set from.</span></span>  
  
    -   <span data-ttu-id="c5b87-122">若要新增包含使用檔案總管] 中的 XML 文件的文字檔案，請按一下 [**從檔案新增**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-122">To add text files that contain XML documents by using File Explorer, click **Add from File**.</span></span>  
  
    -   <span data-ttu-id="c5b87-123">若要新增的 HTTP 位址的 XML 文件，請按一下 **從 Web 加入**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-123">To add an XML document from an HTTP address, click **Add from Web**.</span></span>  
  
    -   <span data-ttu-id="c5b87-124">若要複製或輸入至精靈的 XML 文件的內容，請按一下 **輸入或貼上 XML**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-124">To copy or type the contents of an XML document into the wizard, click **Type or paste XML**.</span></span>  
  
5.  <span data-ttu-id="c5b87-125">當您指定您想要推斷 XML 結構描述集，請按一下的所有 XML 文件來源**確定**來推斷 XML 結構描述設定。</span><span class="sxs-lookup"><span data-stu-id="c5b87-125">When you have specified all the XML document sources from which you want to infer the XML schema set, click **OK** to infer the XML schema set.</span></span> <span data-ttu-id="c5b87-126">結構描述集合會儲存在您的專案資料夾中一個或多個 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-126">The schema set is saved in your project folder in one or more XSD files.</span></span> <span data-ttu-id="c5b87-127">（如結構描述中每個 XML 命名空間，檔案會建立）。</span><span class="sxs-lookup"><span data-stu-id="c5b87-127">(For each XML namespace in the schema, a file is created.)</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a><span data-ttu-id="c5b87-128">若要使用結構描述推斷 Visual Studio XML 編輯器建立 XSD 結構描述檔案的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="c5b87-128">To create an XSD schema file for an XML file by using schema inference in the Visual Studio XML Editor</span></span>  
  
1.  <span data-ttu-id="c5b87-129">編輯 Visual Studio XML 設計工具中的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-129">Edit the XML file in the Visual Studio XML Designer.</span></span>  
  
2.  <span data-ttu-id="c5b87-130">當游標位於 XML 檔案中， **XML**功能表隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c5b87-130">When the cursor is somewhere in the XML file, the **XML** menu appears.</span></span> <span data-ttu-id="c5b87-131">按一下  **Create Schema**上**XML**功能表。</span><span class="sxs-lookup"><span data-stu-id="c5b87-131">Click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="c5b87-132">從 XML 檔案推斷 XSD 結構描述所建立 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-132">An XSD file is created from XSD schema inferred from the XML file.</span></span>  
  
3.  <span data-ttu-id="c5b87-133">將 XSD 結構描述檔案儲存。</span><span class="sxs-lookup"><span data-stu-id="c5b87-133">Save the XSD schema file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5b87-134">從多個預期會有相同的結構描述的 XML 文件，可能會推斷出不同的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c5b87-134">Different XSD schemas might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="c5b87-135">這可能會發生在一個 XML 檔案，而不是在另一個，找到特定項目和屬性或元素，例如包含不同的順序。</span><span class="sxs-lookup"><span data-stu-id="c5b87-135">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="c5b87-136">當您使用 XSD 結構描述推斷時，您應該檢閱推斷的 XSD 結構描述的完整性與正確性。</span><span class="sxs-lookup"><span data-stu-id="c5b87-136">You should review inferred XSD schemas for completeness and accuracy when you use XSD schema inference.</span></span>  
  
#### <a name="to-include-an-xsd-schema-file"></a><span data-ttu-id="c5b87-137">要包含的 XSD 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="c5b87-137">To include an XSD schema file</span></span>  
  
-   <span data-ttu-id="c5b87-138">根據預設，您無法看到 Visual Basic 專案中的 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-138">By default, you cannot see XSD files in Visual Basic projects.</span></span> <span data-ttu-id="c5b87-139">如果 XSD 檔案已包含在專案資料夾中，按一下 [**顯示所有檔案**按鈕**方案總管] 中**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-139">If your XSD file is already included in the folders for your project, click the **Show All Files** button in **Solution Explorer**.</span></span> <span data-ttu-id="c5b87-140">找出 XSD 檔案中的**方案總管 中**，以滑鼠右鍵按一下檔案，然後按一下**將檔案加入至專案中**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-140">Locate the XSD file in **Solution Explorer**, right-click the file, and click **Include File in Project**.</span></span>  
  
-   <span data-ttu-id="c5b87-141">如果 XSD 檔案已不屬於您專案中**方案總管] 中**，以滑鼠右鍵按一下您要儲存 XSD 檔，指向的資料夾**新增**，然後按一下 [**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-141">If your XSD file is not already part of your project, in **Solution Explorer**, right-click the folder in which you want to store the XSD file, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="c5b87-142">找出 XSD 檔案，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-142">Locate your XSD file and then click **Add**.</span></span>  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a><span data-ttu-id="c5b87-143">若要匯入 XML 命名空間中的程式碼檔案</span><span class="sxs-lookup"><span data-stu-id="c5b87-143">To import an XML namespace in a code file</span></span>  
  
1.  <span data-ttu-id="c5b87-144">識別從 XSD 結構描述的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="c5b87-144">Identify the target namespace from your XSD schema.</span></span>  
  
2.  <span data-ttu-id="c5b87-145">在程式碼檔案的開頭，新增`Imports`陳述式的目標 XML 命名空間，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c5b87-145">At the beginning of the code file, add an `Imports` statement for the target XML namespace, as shown in the following example.</span></span>  
  
     <span data-ttu-id="c5b87-146">[!code-vb[VbXMLSamples #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c5b87-146">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span></span>  
  
     <span data-ttu-id="c5b87-147">若要匯入 XML 命名空間當做預設命名空間，也就是套用至 XML 元素和屬性，並沒有命名空間前置詞的命名空間加入`Imports`陳述式的目標預設 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c5b87-147">To import an XML namespace as the default namespace, that is, the namespace that is applied to XML elements and attributes that do not have a namespace prefix, add an `Imports` statement for the target default XML namespace.</span></span> <span data-ttu-id="c5b87-148">請勿指定命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c5b87-148">Do not specify a namespace prefix.</span></span> <span data-ttu-id="c5b87-149">下列是範例`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c5b87-149">Following is an example of an `Imports` statement.</span></span>  
  
     <span data-ttu-id="c5b87-150">[!code-vb[VbXmlSamples #&50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c5b87-150">[!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span></span>  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a><span data-ttu-id="c5b87-151">若要匯入專案中的所有檔案的 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="c5b87-151">To import an XML namespace for all files in a project</span></span>  
  
1.  <span data-ttu-id="c5b87-152">XML 命名空間中的程式碼檔案匯入適用於該程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="c5b87-152">An XML namespace imported in a code file applies to that code file only.</span></span> <span data-ttu-id="c5b87-153">要匯入適用於所有專案中的程式碼檔案的 XML 命名空間，請按兩下，[專案設計工具開啟**我的專案**中**方案總管] 中**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-153">To import an XML namespace that applies to all code files in a project, open the Project Designer by double-clicking **My Project** in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="c5b87-154">在**參考**索引標籤的**匯入命名空間**方塊中，輸入完整的 XML 命名空間宣告的形式的目標 XML 命名空間 (例如， `<xmlns: ns="http://sampleNamespace">`)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-154">On the **References** tab, in the **Imported namespaces** box, type the target XML namespace in the form of a full XML namespace declaration (for example, `<xmlns: ns="http://sampleNamespace">`).</span></span> <span data-ttu-id="c5b87-155">如果目標 XML 命名空間中沒有指定命名空間前置詞，命名空間會在專案的預設 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c5b87-155">If the target XML namespace does not specify a namespace prefix, the namespace will be the default XML namespace for the project.</span></span>  
  
3.  <span data-ttu-id="c5b87-156">按一下 **加入使用者匯入**。</span><span class="sxs-lookup"><span data-stu-id="c5b87-156">Click **Add User Import**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b87-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5b87-157">See Also</span></span>  
 <span data-ttu-id="c5b87-158">[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="c5b87-158">[Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="c5b87-159"> [專案設計工具、參考頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="c5b87-159"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="c5b87-160"> [在 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span><span class="sxs-lookup"><span data-stu-id="c5b87-160"> [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span></span>

