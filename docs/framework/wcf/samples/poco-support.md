---
title: POCO 支援
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183422"
---
# <a name="poco-support"></a>POCO 支援
這個範例會示範對未標記型別的序列化支援，此種型別就是尚未套用序列化屬性的型別，有時亦稱為「簡單的 CLR 物件」(Plain Old CLR Object，POCO) 型別。 推斷<xref:System.Runtime.Serialization.DataContractSerializer>具有無參數建構函式的所有公共無標記類型的資料協定。 資料合約可以讓您在服務間來回傳遞結構化資料。 有關未標記類型的詳細資訊，請參閱[可序列化類型](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
 此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，但使用複數而不是原始數數值型別。 它還類似于[基本資料協定](../../../../docs/framework/wcf/samples/basic-data-contract.md)示例，只不過 不使用 和<xref:System.Runtime.Serialization.DataContractAttribute><xref:System.Runtime.Serialization.DataMemberAttribute>屬性。  
  
 服務是由網際網路資訊服務 (IIS) 所裝載，而用戶端是主控台應用程式 (.exe)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 `ComplexNumber` 類別是在 `ServiceContract` 中使用。 `ComplexNumber` 型別沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)，如下列範例程式碼所示。 依預設，所有公用屬性 (Property) 和欄位都會經過序列化。  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [可序列化類型](../../../../docs/framework/wcf/feature-details/serializable-types.md)
