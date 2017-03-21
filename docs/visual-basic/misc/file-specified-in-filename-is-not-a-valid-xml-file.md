---
title: "檔案名稱中指定的檔案不是有效的 XML 檔案 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2fa595ab411fdd300327db9e1fcca1e3156c7eed
ms.lasthandoff: 03/13/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>檔案名稱中指定的檔案不是有效的 XML 檔案
您提供的檔案名稱不是有效的 XML 檔案。 若要指定 XML 文件所允許的結構和內容，您可以使用文件類型定義 (DTD)、Microsoft XDR (XML-Data Reduced) 結構描述或 XML 結構描述定義語言 (XSD) 結構描述。 XSD 結構描述是較好的方式來指定 XML 文法中的[!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)]。  
  
> [!NOTE]
>  在某些舊版 Visual Studio 中， **XML 設計工具** 是具類型資料集和 XML 結構描述的設計工具。 **XML 設計工具** 仍可用來建立及編輯 XML 結構描述檔案。 不過，在[!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)]，用於建立及編輯具類型資料集設計工具是**Dataset 設計工具**。 如需詳細資訊，請參閱[建立和編輯具類型資料集](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確認您提供的檔案名稱正確。  
  
-   將您要檢查的 XML 檔案載入 **XML 設計工具**，以檢查指定的檔案是否包含有效的 XML。 從 [XML] **** 功能表按一下 [驗證 XML] ****。 [工作清單] ****中會顯示錯誤。  
  
-   如果 XML 檔案有關聯的 XML 結構描述，請確認項目出現在定義的結構中，而且個別項目的內容符合結構描述中所指定的宣告資料類型。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml></xref:System.Xml>   
 [如何：剖析檔案路徑](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
