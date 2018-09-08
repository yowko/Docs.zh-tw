---
title: 如何：建立 WindowsPrincipal 物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 016f19c7141ebaf9b5c1f03adc263b689489119b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128218"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>如何：建立 WindowsPrincipal 物件
有兩種方式來建立 <xref:System.Security.Principal.WindowsPrincipal> 物件，視程式碼是否必須重複執行以角色為基礎的驗證，還是它只必須執行一次而定。  
  
 如果程式碼必須重複執行以角色為基礎的驗證，下列程序的第一個會產生較少負荷。 程式碼只需要進行一次以角色為基礎的驗證時，您可以使用下列程序的第二個來建立 <xref:System.Security.Principal.WindowsPrincipal> 物件。  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>建立 WindowsPrincipal 物件以進行重複驗證  
  
1.  對由靜態 <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> 屬性傳回的 <xref:System.AppDomain> 物件呼叫 <xref:System.AppDomain.SetPrincipalPolicy%2A> 方法，並傳遞 <xref:System.Security.Principal.PrincipalPolicy> 列舉值給方法，指出新的原則應該是什麼。 支援的值為 <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>、<xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> 和 <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>。 下列程式碼可示範這項方法呼叫。  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  設定原則後，請使用靜態 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性來擷取封裝目前 Windows 使用者的主體。 由於屬性傳回類型是 <xref:System.Security.Principal.IPrincipal>，您必須將結果轉換為 <xref:System.Security.Principal.WindowsPrincipal> 類型。 下列程式碼會將新的 <xref:System.Security.Principal.WindowsPrincipal> 物件初始化為與目前執行緒相關聯之主體的值。  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  建立主體物件之後，您可以數種方法的其中一種來進行驗證。  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>建立 WindowsPrincipal 物件以進行單一驗證  
  
1.  藉由呼叫靜態 <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> 方法初始化新的 <xref:System.Security.Principal.WindowsIdentity> 物件，此方法會查詢目前的 Windows 帳戶，將該帳戶的相關資訊放入新建立的身分識別物件。 下列程式碼會建立新的 <xref:System.Security.Principal.WindowsIdentity> 物件，並將其初始化為目前已驗證的使用者。  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  建立新的 <xref:System.Security.Principal.WindowsPrincipal> 物件，並傳遞在上一個步驟中建立之 <xref:System.Security.Principal.WindowsIdentity> 物件的值給它。  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  建立主體物件之後，您可以數種方法的其中一種來進行驗證。  
  
## <a name="see-also"></a>另請參閱

- [Principal 和 Identity 物件](../../../docs/standard/security/principal-and-identity-objects.md)
