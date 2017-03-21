---
title: "無法寫入輸出檔 &quot;&lt;filename&gt;&quot;:&lt;錯誤&gt;|Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
dev_langs:
- VB
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe093ec3b36ba733cb9b0c162e242c8dce6b7c78
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>無法寫入輸出檔 '&lt;filename&gt;':&lt;錯誤&gt;
建立檔案時發生問題。  
  
 無法開啟輸出檔案以供寫入。 檔案 (或包含檔案的資料夾) 可能已由另一個處理序以獨佔方式開啟使用，或是其可能設定了唯讀屬性。  
  
 以獨佔方式開啟檔案的常見狀況有：  
  
-   應用程式已在執行中，且正在使用其檔案。 若要解決此問題，請確定應用程式不在執行中。  
  
-   另一個應用程式已開啟該檔案。 若要解決此問題，請確定沒有其他應用程式正在存取檔案。 您不一定能顯而易見地分辨出是哪個應用程式在存取您的檔案；在這種情況下，重新啟動電腦可能是終止該應用程式最容易的方法。  
  
 即使是其中一個專案輸出檔被標為唯讀，都會擲回這個例外狀況。  
  
 **錯誤識別碼︰** BC31019  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  再次編譯程式，看看錯誤是否重複發生。  
  
2.  如果錯誤繼續發生，請儲存您的工作，然後重新啟動 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。  
  
3.  如果錯誤繼續發生，請重新啟動電腦。  
  
4.  如果問題重複發生，請重新安裝 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
5.  如果錯誤在重新安裝之後持續發生，請通知 Microsoft 產品支援服務。  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>在檔案總管中檢查檔案屬性  
  
1.  開啟您感興趣的資料夾。  
  
2.  按一下 **檢視**圖示，然後選擇**詳細資料**。  
  
3.  以滑鼠右鍵按一下資料行標頭，然後選擇 **屬性**從下拉式清單。  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>變更檔案或資料夾的屬性  
  
1.  在**檔案總管**，以滑鼠右鍵按一下檔案或資料夾，然後選擇 **屬性**。  
  
2.  在**屬性**區段**一般**索引標籤上，清除**唯讀**方塊。  
  
3.  Press **OK**.  
  
## <a name="see-also"></a>另請參閱  
 [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
