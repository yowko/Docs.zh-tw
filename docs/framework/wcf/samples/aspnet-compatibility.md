---
title: ASP.NET 相容性
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: e9566c24756afef98c8594c8d7b542bd2ad1e5b5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045175"
---
# <a name="aspnet-compatibility"></a>ASP.NET 相容性

這個範例會示範如何在 Windows Communication Foundation (WCF) 中啟用 ASP.NET 相容性模式。 在 ASP.NET 相容性模式中執行的服務會完全參與 ASP.NET 應用程式管線, 並可利用檔案/URL 授權、會話狀態和<xref:System.Web.HttpContext>類別等 ASP.NET 功能。 <xref:System.Web.HttpContext>類別可讓您存取 cookie、會話和其他 ASP.NET 功能。 這個模式會要求這些繫結使用 HTTP 傳輸，而且服務本身必須以 IIS 裝載。

在這個範例中，用戶端是主控台應用程式 (可執行檔)，而服務則是由網際網路資訊服務 (IIS) 裝載。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

這個範例需要 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 應用程式集區才能執行。 若要建立應用程式集區，或是修改預設的應用程式集區，請遵循下列步驟。

1. 開啟 [**控制台**]。  開啟 [**系統及安全性**] 標題下的 [系統**管理工具**] 小程式。 開啟 [ **Internet Information Services (IIS) 管理員**] 小程式。

2. 展開 [**連接**] 窗格中的 treeview。 選取 [**應用程式**集區] 節點。

3. 若要將預設應用程式集區[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]設定為使用 (這可能會造成與現有網站不相容的問題), 請以滑鼠右鍵按一下 [ **DefaultAppPool** ] 清單專案, 然後選取 [**基本設定**]。 將  **.Net Framework 版本** 下拉設定為  **.net framework v v4.0.30128** (或更新版本)。

4. 若要建立使用[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (以保留其他應用程式的相容性) 的新應用程式集區, 請以滑鼠右鍵按一下 [**應用程式**集區] 節點, 然後選取 [**新增應用程式集**區 ...]。 將新的應用程式集區命名為, 然後將 **.Net Framework 版本**向下提取至 **.net framework v v4.0.30128** (或更新版本)。 執行下列設定步驟之後, 以滑鼠右鍵按一下**ServiceModelSamples**應用程式, 然後選取 [**管理應用程式**]、[**高級設定**]。 將**應用程式**集區設定為新的應用程式集區。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

這個範例是以執行計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。 `ICalculator` 合約已修改成允許執行一組作業的 `ICalculatorSession` 合約，並同時保留執行結果。

```csharp
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

服務會使用 ASP.NET 會話來儲存每個用戶端會話的結果。 這樣服務便可在跨多個服務呼叫時維護每個工作階段的執行結果。

> [!NOTE]
> ASP.NET 會話狀態和 WCF 會話是非常不同的事。 如需 WCF 會話的詳細資訊, 請參閱[會話](../../../../docs/framework/wcf/samples/session.md)。

服務具有 ASP.NET 會話狀態的相關資訊, 而且需要 ASP.NET 相容性模式才能正常運作。 這些需求會在套用 `AspNetCompatibilityRequirements` 屬性時以宣告方式表達。

```csharp
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

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。

3. 建立解決方案之後, 請執行 Setup .bat 來設定 IIS 7.0 中的 ServiceModelSamples 應用程式。 ServiceModelSamples 目錄現在應該會顯示為 IIS 7.0 應用程式。

4. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。

## <a name="see-also"></a>另請參閱

- [AppFabric 裝載和持續性範例](https://go.microsoft.com/fwlink/?LinkId=193961)
