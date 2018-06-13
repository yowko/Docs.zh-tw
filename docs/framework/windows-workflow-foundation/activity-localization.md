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
# <a name="activity-localization"></a><span data-ttu-id="5ba4f-102">活動當地語系化</span><span class="sxs-lookup"><span data-stu-id="5ba4f-102">Activity Localization</span></span>
<span data-ttu-id="5ba4f-103">若可能需要將工作流程應用程式與元件當地語系化為其他文化特性和語言，則應使用資源字串，如此一來，不需重新編譯，即可當地語系化這些應用程式與元件。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="5ba4f-104">活動當地語系化</span><span class="sxs-lookup"><span data-stu-id="5ba4f-104">Activity Localization</span></span>  
 <span data-ttu-id="5ba4f-105">如同所有必須當地語系化的應用程式 (針對不同語言和文化特性的不同版本而發行)，所有對使用者顯示的字串都不可直接放在程式碼中，而應儲存在資源檔中。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="5ba4f-106">然後可以透過存取這些字串<!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="5ba4f-107">如果您要開發以數種語言散佈的元件，也可以將資源字串用於活動驗證訊息、使用者定義的追蹤資料、追蹤訊息，以及錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="5ba4f-108">下列練習示範如何使用資源檔。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="5ba4f-109">使用資源檔做為當地語系化字串</span><span class="sxs-lookup"><span data-stu-id="5ba4f-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="5ba4f-110">在[!INCLUDE[vs2010](../../../includes/vs2010-md.md)]，以滑鼠右鍵按一下您的專案中**方案總管 中**選取**新增...**，**新項目...**.</span><span class="sxs-lookup"><span data-stu-id="5ba4f-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="5ba4f-111">選取**資源檔**和檔案命名為 ErrorResources.resx。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="5ba4f-112">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="5ba4f-113">開啟資源檔。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-113">Open the resource file.</span></span> <span data-ttu-id="5ba4f-114">新增項目與**名稱**為 ErrorString 和**值**的 「 活動無效。 」</span><span class="sxs-lookup"><span data-stu-id="5ba4f-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="5ba4f-115">將下列 `using` 陳述式加入至類別中。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="5ba4f-116">在專案中建立資料管理員。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="5ba4f-117">視需要從資源管理員取得字串。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="5ba4f-118">下列程式碼範例示範如何在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法中利用已當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="5ba4f-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
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
