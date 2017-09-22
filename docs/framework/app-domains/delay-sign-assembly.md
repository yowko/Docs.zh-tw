---
title: "延遲簽署組件"
ms.date: 07/31/2017
ms.prod: .net-framework
ms.technology:
- dotnet-bcl
ms.topic: article
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 0ee5fed355e0d8418500f1ecee53019548d9f7f8
ms.openlocfilehash: 2c50a652c834dba80595f2ea419bc75148e13419
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# 延遲簽署組件
組織可以使用嚴密保護的金鑰組，即使開發人員都無法每天存取。  開發人員通常使用公開金鑰，但只有少數人才能存取私密金鑰。  開發具有強式名稱的組件時，每一個參考強式名稱目標組件的組件都會含有公開金鑰語彙基元，可提供目標組件強式名稱。  這項功能的前提是可以在開發處理序期間使用公開金鑰。  
  
 您可以在建置時間使用延遲或部分簽署，以保留強式名稱簽章的可移植執行檔 \(PE\) 空間，但這項作業會將實際簽署的時間推延到稍後的階段 \(通常是在組件出貨之前\)。  
  
 下列步驟概略說明延遲簽署組件的程序：  
  
1.  從完成最後簽署的組織中取得金鑰組的公開金鑰部分。  通常這個金鑰是 .snk 檔案格式，您可以使用 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供的[強式名稱工具 \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 來建立該檔案。  
  
2.  使用來自 <xref:System.Reflection> 的兩個自訂屬性註解組件的原始程式碼：  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>，將含有公開金鑰的檔名當做引數傳遞給其建構函式。  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>，指出延遲簽署正在使用中，方法是將 **true** 當做引數傳遞給其建構函式。  例如：  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  編譯器將公開金鑰插入組件資訊清單，並且保留 PE 檔的空間供完整強式名稱簽章使用。  真正的公開金鑰必須在建置組件時儲存起來，這樣一來參考這個組件的其他組件便可取得金鑰，並將其儲存在自己的組件參考中。  
  
4.  由於組件沒有有效的強式名稱簽章，因此必須關閉該簽章的驗證。  您可以使用 **\-Vr** 選項和強式名稱工具來進行這項作業。  
  
     下列範例關閉 `myAssembly.dll` 組件的驗證。  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     如要關閉您無法執行的強式名稱工具，例如 Advanced RISC 電腦 \(ARM\) 微處理器為，請使用 **–Vk** 選項建立登錄檔平台的驗證。  匯入登錄檔到您要關閉驗證之電腦上的登錄。  下列範例會建立 `myAssembly.dll`的登錄檔。  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     使用 **–Vr** 或 **–Vk** 選項，您可以選擇性地包含測試金鑰簽署的 .snk 檔案。  
  
    > [!WARNING]
    > 請勿依賴強式名稱提供安全性。 強式名稱僅提供唯一識別。
  
    > [!NOTE]
    >  如果您在開發時於 64 位元的電腦上使用延遲簽署搭配 Visual Studio，並針對 \[**任何 CPU**\] 編譯組件，您可能必須套用 **\-Vr** 選項兩次 \(在 Visual Studio 中，\[**任何 CPU**\] 為 \[**平台目標**\] 建置屬性的值；當您從命令列進行編譯時，這就是預設值\)。若要從命令列或從 \[Windows 檔案總管\] 執行您的應用程式，請使用 64 位元版的[Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)將 **\-Vr** 選項套用到組件。  若要在設計階段將組件載入 Visual Studio 中 \(例如，若組件包含您應用程式中其他組件所使用的元件\)，請使用 32 位元版的強式名稱工具。  這是因為 Just\-In\-Time \(JIT\) 編譯器會將組件編譯成 64 位元的機器碼 \(若從命令列執行組件\)，以及編譯成 32 位元的機器碼 \(若將組件載入設計階段環境中\)。  
  
5.  接下來 \(通常是在交出產品之前\)，您將組件送至組織的簽署授權單位，使用 **\-R** 選項和強式命名工具進行實際的強式名稱簽署。  
  
     下列範例使用 `sgKey.snk` 金鑰組將 `myAssembly.dll` 組件簽署為強式名稱。  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## 請參閱  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)   
 [如何：建立公開/私密金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)   
 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)

