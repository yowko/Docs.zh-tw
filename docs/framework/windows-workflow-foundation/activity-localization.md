---
title: 活動當地語系化
ms.date: 03/30/2017
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
ms.openlocfilehash: 23a6d5c2ed202f030397eb70382896468a68a724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512459"
---
# <a name="activity-localization"></a>活動當地語系化
若可能需要將工作流程應用程式與元件當地語系化為其他文化特性和語言，則應使用資源字串，如此一來，不需重新編譯，即可當地語系化這些應用程式與元件。  
  
## <a name="activity-localization"></a>活動當地語系化  
 如同所有必須當地語系化的應用程式 (針對不同語言和文化特性的不同版本而發行)，所有對使用者顯示的字串都不可直接放在程式碼中，而應儲存在資源檔中。 然後可以透過存取這些字串<!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`。 如果您要開發以數種語言散佈的元件，也可以將資源字串用於活動驗證訊息、使用者定義的追蹤資料、追蹤訊息，以及錯誤訊息。  
  
 下列練習示範如何使用資源檔。  
  
#### <a name="using-resource-files-for-localized-strings"></a>使用資源檔做為當地語系化字串  
  
1.  在[!INCLUDE[vs2010](../../../includes/vs2010-md.md)]，以滑鼠右鍵按一下您的專案中**方案總管 中**選取**新增...**，**新項目...**.  
  
2.  選取**資源檔**和檔案命名為 ErrorResources.resx。 按一下 [加入] 。  
  
3.  開啟資源檔。 新增項目與**名稱**為 ErrorString 和**值**的 「 活動無效。 」  
  
4.  將下列 `using` 陳述式加入至類別中。  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  在專案中建立資料管理員。  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  視需要從資源管理員取得字串。  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 下列程式碼範例示範如何在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法中利用已當地語系化的字串。  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
