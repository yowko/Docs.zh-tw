---
title: "延遲簽署組件 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2fce2174da6b5d954e0197d7c834289070c09a22
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
<a id="delay-signing-an-assembly" class="xliff"></a>

# 延遲簽署組件
組織可能會有開發人員無法每日存取的嚴密保護金鑰組。 公開金鑰經常都可以使用，但只有少數人才能存取私密金鑰。 在以強式名稱開發組件時，每個參考強式名稱目標組件的組件都包含用來指定目標組件的強式名稱的公開金鑰語彙基元。 這需要可在開發程序期間使用公開金鑰。  
  
 您可以在建置階段中使用延遲或部分簽署，以便在可攜式執行檔 (PE) 中保留強式名稱簽章的空間，但延後到之後的某個階段 (通常是就在傳送組件之前) 才實際簽署。  
  
 下列步驟概述延遲簽署組件的程序：  
  
1.  從將執行最終簽署的組織取得金鑰組的公開金鑰部分。 此金鑰通常格式為 .snk 檔案，這可以使用 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供的[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)建立。  
  
2.  使用來自 <xref:System.Reflection> 的兩個自訂屬性為組件的原始碼加上註解：  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>，它會將傳遞包含公開金鑰的檔案名稱，作為其建構函式的參數。  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>，它指出正在藉由傳遞 **true** 作為其建構函式的參數來使用延遲簽署。 例如:   
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]  [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]  [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  編譯器會將公開金鑰插入到組件資訊清單，並在 PE 檔中保留完整強式名稱簽章的空間。 在建置組件時必須儲存真正的公開金鑰，以便參考這個組件的其他組件可以取得金鑰，儲存在它們自己的組件參考。  
  
4.  因為組件沒有有效的強式名稱簽章，所以該簽章的驗證作業必須關閉。 您可以使用 **-Vr** 選項搭配強式名稱工具完成此作業。  
  
     下列範例會關閉 `myAssembly.dll` 組件的驗證。  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     若要在您無法在執行強式名稱工具的平台上關閉驗證，例如 Advanced RISC Machine (ARM) 微處理器，請使用 **– Vk** 選項來建立登錄檔。 將登錄檔匯入到您要關閉驗證的電腦上的登錄。 下列範例將建立 `myAssembly.dll` 的登錄檔。  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     使用 **-Vr** 或 **– Vk** 選項時，您可以選擇性地包含測試金鑰簽署的 .snk 檔案。  
  
    > [!CAUTION]
    >  **-Vr** 或 **–Vk** 選項僅供開發期間使用。 將組件加入至略過驗證清單會使安全性變弱。 具有惡意的組件可能使用加入至略過驗證清單之組件的完全指定組件名稱 (組件名稱、版本、文化特性和公開金鑰語彙基元)，以偽裝其識別 (Identity)。 這會使具有惡意的組件也略過驗證。  
  
    > [!NOTE]
    >  如果您在 64 位元電腦上，使用 Visual Studio 進行開發期間使用延遲簽署，並且編譯**任何 CPU** 的組件，您可能要套用 **-Vr** 選項兩次。 (在 Visual Studio 中，**任何 CPU** 是**平台目標**建置屬性的值，當您從命令列編譯時，它是預設值。)若要從命令列或檔案總管執行您的應用程式，請使用 64 位元版本的 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 套用 **-Vr** 選項給組件。 若要在設計階段將組件載入到 Visual Studio (例如，如果組件包含您應用程式中其他組件使用的元件)，請使用 32 位元版本的強式名稱工具。 這是因為當組件是從命令列執行時，just-in-time (JIT) 編譯器會將組件編譯為 64 位元原生程式碼，而當載入到設計階段環境時，編譯為 32 位元原生程式碼。  
  
5.  稍後，通常就在傳送之前，您會將組件送出給貴組織的簽署授權單位，以便使用強式名稱工具的 **–R** 選項進行實際的強式名稱簽署。  
  
     下列範例會使用 `myAssembly.dll` 金鑰組，將組件 `sgKey.snk` 簽署為強式名稱。  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
<a id="see-also" class="xliff"></a>

## 另請參閱  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)   
 [如何：建立公開/私密金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)   
 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
