---
title: "檔案名稱中指定的檔案不是有效的 XML 檔案 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8b46b9d896f0dce401992e8a20e040b85091ba5d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="fd264-102">檔案名稱中指定的檔案不是有效的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="fd264-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="fd264-103">您提供的檔案名稱不是有效的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="fd264-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="fd264-104">若要指定 XML 文件所允許的結構和內容，您可以使用文件類型定義 (DTD)、Microsoft XDR (XML-Data Reduced) 結構描述或 XML 結構描述定義語言 (XSD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="fd264-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="fd264-105">XSD 結構描述是較好的方式來指定 XML 文法中的[!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fd264-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd264-106">在某些舊版 Visual Studio 中， **XML 設計工具** 是具類型資料集和 XML 結構描述的設計工具。</span><span class="sxs-lookup"><span data-stu-id="fd264-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="fd264-107">**XML 設計工具** 仍可用來建立及編輯 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="fd264-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="fd264-108">不過，在[!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)]，用於建立及編輯具類型資料集設計工具是**Dataset 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="fd264-108">However, in [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="fd264-109">如需詳細資訊，請參閱[建立和編輯具類型資料集](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets)。</span><span class="sxs-lookup"><span data-stu-id="fd264-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd264-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fd264-110">To correct this error</span></span>  
  
-   <span data-ttu-id="fd264-111">確認您提供的檔案名稱正確。</span><span class="sxs-lookup"><span data-stu-id="fd264-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="fd264-112">將您要檢查的 XML 檔案載入 **XML 設計工具**，以檢查指定的檔案是否包含有效的 XML。</span><span class="sxs-lookup"><span data-stu-id="fd264-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="fd264-113">從 [XML] **** 功能表按一下 [驗證 XML] ****。</span><span class="sxs-lookup"><span data-stu-id="fd264-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="fd264-114">[工作清單] ****中會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd264-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="fd264-115">如果 XML 檔案有關聯的 XML 結構描述，請確認項目出現在定義的結構中，而且個別項目的內容符合結構描述中所指定的宣告資料類型。</span><span class="sxs-lookup"><span data-stu-id="fd264-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd264-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd264-116">See Also</span></span>  
 <span data-ttu-id="fd264-117"><xref:System.Xml></xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="fd264-117"><xref:System.Xml></span></span>   
<span data-ttu-id="fd264-118"> [如何：剖析檔案路徑](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span><span class="sxs-lookup"><span data-stu-id="fd264-118"> [How to: Parse File Paths](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span></span>
