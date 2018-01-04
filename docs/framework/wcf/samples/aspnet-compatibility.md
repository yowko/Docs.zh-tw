---
title: "ASP.NET 相容性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751fe96caa2be63e925b3107fa2c198b523bef72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-compatibility"></a>ASP.NET 相容性
這個範例會示範如何在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 中啟用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 相容模式。 在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 相容模式中執行的服務會完全參與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式管線，並且會利用像是檔案/URL 授權、工作階段狀態，以及 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 類別等 <xref:System.Web.HttpContext> 功能。 <xref:System.Web.HttpContext> 類別允許存取 Cookie、工作階段以及其他 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 功能。 這個模式會要求這些繫結使用 HTTP 傳輸，而且服務本身必須以 IIS 裝載。  
  
 在這個範例中，用戶端是主控台應用程式 (可執行檔)，而服務則是由網際網路資訊服務 (IIS) 裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!NOTE]
>  這個範例需要 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 應用程式集區才能執行。 若要建立應用程式集區，或是修改預設的應用程式集區，請遵循下列步驟。  
>   
>  1.  開啟**控制台**。  開啟**系統管理工具**下方的小程式**系統及安全性**標題。 開啟**網際網路資訊服務 (IIS) 管理員**小程式。  
> 2.  展開的 treeview**連線**窗格。 選取**應用程式集區**節點。  
> 3.  若要設定要使用的預設應用程式集區[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（這會導致與現有站台不相容問題），以滑鼠右鍵按一下**DefaultAppPool**清單項目，然後選取**基本設定...**. 設定**.Net Framework 版本**提取向**.Net Framework v4.0.30128** （或更新版本）。  
> 4.  若要建立新的應用程式集區使用[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]（以保留與其他應用程式相容性），以滑鼠右鍵按一下**應用程式集區**節點，然後選取**新增應用程式集區...**. 為新的應用程式集區，並設定**.Net Framework 版本**提取向**.Net Framework v4.0.30128** （或更新版本）。 下面執行安裝程式步驟之後，以滑鼠右鍵按一下**ServiceModelSamples**應用程式並選取**管理應用程式**，**進階設定...**. 設定**應用程式集區**新的應用程式集區。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作計算機服務。 `ICalculator` 合約已修改成允許執行一組作業的 `ICalculatorSession` 合約，並同時保留執行結果。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 此服務會維護用戶端的狀態 (方法是使用該功能)，因為在進行計算時已呼叫了多個服務作業。 用戶端會呼叫 `Result` 以擷取目前的結果，並且能夠呼叫 `Clear` 將結果清除為零。  
  
 服務會使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 工作階段來儲存每個用戶端工作階段的結果。 這樣服務便可在跨多個服務呼叫時維護每個工作階段的執行結果。  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 工作階段狀態與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段是完全不同的項目。  請參閱[工作階段](../../../../docs/framework/wcf/samples/session.md)如需詳細資訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]工作階段。  
  
 服務對 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 工作階段狀態有相當深的相依性，並且需要 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 相容性模式才能正確運作。 這些需求會在套用 `AspNetCompatibilityRequirements` 屬性時以宣告方式表達。  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  在建立方案後，執行 Setup.bat 以便在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中安裝 ServiceModelSamples 應用程式。 ServiceModelSamples 目錄現在應該會顯示為 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
