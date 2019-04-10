---
title: 使用序列化繫結器
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 47a1974386927316ea9230ec27cf647d7245c44a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329839"
---
# <a name="usage-of-serialization-binder"></a>使用序列化繫結器
此範例示範如何使用 <xref:System.Runtime.Serialization.SerializationBinder> 變更序列化時一般類型的版本。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>討論  
 此範例示範目標為不同版本之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的兩個實體如何使用 Binary Formatter 和序列化繫結器進行通訊。  
  
 此範例的開發已經使用 .NET Remoting 完成。 此範例由目標為 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 且實作具有一般類型之合約的一個伺服器，以及兩個不同的用戶端 (一個目標為 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 而另一個目標為 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]) 所組成。  
  
 伺服器會將 <xref:System.Runtime.Serialization.SerializationBinder> 附加到 Binary Formatter 以便能夠根據序列化變更型別的版本，因此，兩個用戶端都可以正確還原序列化這些型別。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1. 若要執行用戶端，以滑鼠右鍵按一下 sbgenericsvts （6 個專案），然後選取**屬性**。  
  
2. 在 **通用屬性**，選取**啟始專案**，然後選取**多個啟始專案**。  
  
3. 選取 **伺服器**第一，然後**Client20** ，然後**Client40**。 選取 **開始**這三個動作專案，並保留其餘設定為**無**。  
  
4. 按一下 **確定**，然後按 F5 執行範例。
