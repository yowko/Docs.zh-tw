---
title: 逐步解說：建立可延伸應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292447fa3cf2dbad70dbfef32b7c184b250ed25e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a>逐步解說：建立可延伸應用程式
本逐步解說描述如何建立會執行簡單的計算機功能的增益集的管線。 不會示範真實世界的實例。相反地，它會示範在管線，以及如何增益集可以提供主機服務的基本功能。  
  
 本逐步解說將說明下列工作：  
  
-   建立 Visual Studio 方案。  
  
-   建立管線目錄結構。  
  
-   正在建立的合約和檢視表。  
  
-   建立增益集端配接器。  
  
-   建立主應用程式端配接器。  
  
-   建立主機。  
  
-   建立增益集。  
  
-   部署管線。  
  
-   執行主應用程式。  
  
 此管線傳遞僅可序列化的型別 (<xref:System.Double>和<xref:System.String>)、 主機和增益集之間。 如需示範如何將複雜資料型別集合的範例，請參閱[逐步解說： 將傳遞主機集合與增益集](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)。  
  
 這個管線的合約會定義四個的算術運算的物件模型： 加入、 減、 乘、 和分割。 使用公式來計算，例如 2 + 2，主機會提供增益集和增益集傳回結果至主機。  
  
 第 2 版的計算機增益集提供更多計算的可能性，並示範版本控制。 中描述[逐步解說： 為您的主機變更啟用回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列項目才能完成本逐步解說：  
  
-   Visual Studio。  
  
## <a name="creating-a-visual-studio-solution"></a>建立 Visual Studio 方案  
 使用 Visual Studio 中的解決方案，以包含管線區段的專案。  
  
#### <a name="to-create-the-pipeline-solution"></a>若要建立管線方案  
  
1.  在 Visual Studio 中，建立新的專案，名為`Calc1Contract`。 它的基礎**類別庫**範本。  
  
2.  將方案命名`CalculatorV1`。  
  
## <a name="creating-the-pipeline-directory-structure"></a>建立管線目錄結構  
 增益集模型要求管線區段組件應置於指定的目錄結構。 如需管線結構的詳細資訊，請參閱[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>若要建立管線目錄結構  
  
1.  在您的電腦上的任何位置建立應用程式資料夾。  
  
2.  在該資料夾中建立下列結構：  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     不需要將管線資料夾結構放在應用程式資料夾。完成以下只是為了方便起見。 在適當的步驟，逐步解說會說明如何變更程式碼，如果管線資料夾結構是在不同的位置。 請參閱中的管線目錄需求的討論[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
    > [!NOTE]
    >  `CalcV2`資料夾不是在本逐步解說，它是一個預留位置，如[逐步解說： 為您的主機變更啟用回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)。  
  
## <a name="creating-the-contract-and-views"></a>建立合約和檢視  
 此管線的合約區段會定義`ICalc1Contract`介面，定義四種方法： `add`， `subtract`， `multiply`，和`divide`。  
  
#### <a name="to-create-the-contract"></a>若要建立合約  
  
1.  名為 Visual Studio 方案中`CalculatorV1`，開啟`Calc1Contract`專案。  
  
2.  在**方案總管 中**，加入下列組件的參考`Calc1Contract`專案：  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  在**方案總管 中**，排除加入新的預設類別**類別庫**專案。  
  
4.  在**方案總管 中**，加入新項目加入專案中，使用**介面**範本。 在**加入新項目**對話方塊中，名稱介面`ICalc1Contract`。  
  
5.  在介面檔案中加入命名空間的參考<xref:System.AddIn.Contract>和<xref:System.AddIn.Pipeline>。  
  
6.  您可以使用下列程式碼來完成此合約區段。 請注意，此介面必須<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  （選擇性） 建置的 Visual Studio 方案。 無法執行方案，直到最後的程序，但每個程序可確保每個專案都會後建置更正。  
  
 由於增益集的檢視和主應用程式檢視的增益集通常在相同的程式碼，特別是增益集的第一個版本，您可以輕鬆檢視建立在相同的時間。 它們之間只能有一個因數的差異： 增益集檢視需要<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性，而增益集的 [主機] 檢視不需要任何屬性。  
  
#### <a name="to-create-the-add-in-view"></a>若要建立增益集的檢視  
  
1.  加入新的專案，名為`Calc1AddInView`至`CalculatorV1`方案。 它的基礎**類別庫**範本。  
  
2.  在**方案總管 中**，將參考加入至 System.AddIn.dll`Calc1AddInView`專案。  
  
3.  在**方案總管 中**，排除加入新的預設類別**類別庫**專案，並將新的項目加入至專案，使用**介面**範本。 在**加入新項目**對話方塊中，名稱介面`ICalculator`。  
  
4.  在介面檔案中，加入的命名空間參考<xref:System.AddIn.Pipeline>。  
  
5.  您可以使用下列程式碼來完成此增益集檢視。 請注意，此介面必須<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  （選擇性） 建置的 Visual Studio 方案。  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>若要建立增益集的 [主機] 檢視  
  
1.  加入新的專案，名為`Calc1HVA`至`CalculatorV1`方案。 它的基礎**類別庫**範本。  
  
2.  在**方案總管 中**，排除加入新的預設類別**類別庫**專案，並將新的項目加入至專案，使用**介面**範本。 在**加入新項目**對話方塊中，名稱介面`ICalculator`。  
  
3.  在介面檔案中，使用下列程式碼來完成增益集的 [主機] 檢視。  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-add-in-side-adapter"></a>建立增益集端配接器  
 此增益集端配接器是由一個檢視合約配接器所組成。 這個管線區段轉換從增益集的檢視為合約的型別。  
  
 在此管線中，增益集提供的服務主機，主機，型別從增益集至主機。 由於沒有型別從主機到增益集，您沒有包含此管線的增益集端上的合約來檢視配接器。  
  
#### <a name="to-create-the-add-in-side-adapter"></a>若要建立增益集端配接器  
  
1.  加入新的專案，名為`Calc1AddInSideAdapter`至`CalculatorV1`方案。 它的基礎**類別庫**範本。  
  
2.  在**方案總管 中**，加入下列組件的參考`Calc1AddInSideAdapter`專案：  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  加入相鄰的管線區段的專案的專案參考：  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  選取每個專案參考，然後在**屬性**設定**複製到本機**至**False**。 在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**為兩個專案的參考。  
  
5.  重新命名專案的預設類別`CalculatorViewToContractAddInSideAdapter`。  
  
6.  在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。  
  
7.  在類別檔案中，加入相鄰的區段的命名空間參考：`CalcAddInViews`和`CalculatorContracts`。 (在 Visual Basic 中為這些命名空間參考`Calc1AddInView.CalcAddInViews`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)  
  
8.  套用<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性`CalculatorViewToContractAddInSideAdapter`類別，將其識別為增益集端配接器。  
  
9. 請`CalculatorViewToContractAddInSideAdapter`類別繼承<xref:System.AddIn.Pipeline.ContractBase>，其提供的預設實作<xref:System.AddIn.Contract.IContract>介面，並實作管線的合約介面`ICalc1Contract`。  
  
10. 新增公用建構函式可接受`ICalculator`、 放入快取中的私用欄位，並呼叫基底類別建構函式。  
  
11. 若要實作的成員`ICalc1Contract`，只需呼叫的對應成員`ICalculator`會傳遞至建構函式，並傳回結果的執行個體。 這會調整檢視 (`ICalculator`) 的合約 (`ICalc1Contract`)。  
  
     下列程式碼顯示完整的增益集端配接器。  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-host-side-adapter"></a>建立主應用程式端配接器  
 這個主應用程式端配接器是由一個合約來檢視配接器所組成。 此區段會調整到主機的檢視增益集的合約。  
  
 在此管線中，增益集提供服務給主機和類型流程從增益集至主機。 由於沒有型別從主機到增益集，您不必包括檢視合約介面卡。  
  
 若要實作生命週期管理，請使用<xref:System.AddIn.Pipeline.ContractHandle>物件存留期語彙基元附加的合約。 您必須將此控制代碼的參考在存留期管理工作的順序。 套用語彙基元之後，任何其他程式設計需要不，因為增益集系統可以處置的物件時便不再使用，讓它們可供記憶體回收。 如需詳細資訊，請參閱[生命週期管理](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。  
  
#### <a name="to-create-the-host-side-adapter"></a>若要建立主應用程式端配接器  
  
1.  加入新的專案，名為`Calc1HostSideAdapter`至`CalculatorV1`方案。 它的基礎**類別庫**範本。  
  
2.  在**方案總管 中**，加入下列組件的參考`Calc1HostSideAdapter`專案：  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  加入相鄰的區段的專案的專案參考：  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  選取每個專案參考，然後在**屬性**設定**複製到本機**至**False**。 在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**為兩個專案的參考。  
  
5.  重新命名專案的預設類別`CalculatorContractToViewHostSideAdapter`。  
  
6.  在類別檔案中，加入命名空間參考<xref:System.AddIn.Pipeline>。  
  
7.  在類別檔案中，加入相鄰的區段的命名空間參考：`CalcHVAs`和`CalculatorContracts`。 (在 Visual Basic 中為這些命名空間參考`Calc1HVA.CalcHVAs`和`Calc1Contract.CalculatorContracts`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)  
  
8.  套用<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性`CalculatorContractToViewHostSideAdapter`類別，以識別為主應用程式端配接器區段。  
  
9. 請`CalculatorContractToViewHostSideAdapter`類別實作介面，代表增益集的 [主機] 檢視： `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator`在 Visual Basic 中)。  
  
10. 新增公用建構函式可接受管線的合約型別， `ICalc1Contract`。 建構函式必須快取之合約的參考。 它也必須建立並快取新<xref:System.AddIn.Pipeline.ContractHandle>合約，若要管理的增益集的存留期。  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> ，請務必存留期管理。 如果您無法將參考保留<xref:System.AddIn.Pipeline.ContractHandle>物件，記憶體回收會回收，及管線時您的程式不會預期它會關閉。 這可能會導致錯誤很難進行診斷，例如<xref:System.AppDomainUnloadedException>。 Shutdown 正在正常階段生命週期的管線，因此沒有任何方法的存留期管理程式碼偵測此狀況，會產生錯誤。  
  
11. 若要實作的成員`ICalculator`，只需呼叫的對應成員`ICalc1Contract`會傳遞至建構函式，並傳回結果的執行個體。 這會調整的合約 (`ICalc1Contract`) 檢視 (`ICalculator`)。  
  
     下列程式碼顯示完整的主應用程式端配接器。  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-host"></a>建立主機  
 主應用程式互動的增益集透過增益集的 [主機] 檢視。 它會使用增益集探索與啟用方法所提供<xref:System.AddIn.Hosting.AddInStore>和<xref:System.AddIn.Hosting.AddInToken>類別來執行下列動作：  
  
-   更新快取的管線和增益集的資訊。  
  
-   尋找增益集主機檢視類型的`ICalculator`，指定的管線根目錄下。  
  
-   提示使用者指定的增益集使用。  
  
-   啟用所選增益新應用程式定義域中具有指定之安全性的信任層級。  
  
-   執行自訂`RunCalculator`方法，這個方法會呼叫增益集的增益集的 [主機] 檢視中所指定的方法。  
  
#### <a name="to-create-the-host"></a>若要建立主應用程式  
  
1.  加入新的專案，名為`Calc1Host`至`CalculatorV1`方案。 它的基礎**主控台應用程式**範本。  
  
2.  在**方案總管 中**，加入 System.AddIn.dll 組件的參考`Calc1Host`專案。  
  
3.  將專案參考加入`Calc1HVA`專案。 選取該專案的參考，然後在**屬性**設定**複製到本機**至**False**。 在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**。  
  
4.  重新命名類別檔案 （在 Visual Basic 中的模組） `MathHost1`。  
  
5.  在 Visual Basic 使用**應用程式** 索引標籤**專案屬性**對話方塊來設定**啟始物件**至**Sub Main**。  
  
6.  在類別或模組檔案中，加入的命名空間參考<xref:System.AddIn.Hosting>。  
  
7.  在類別或模組檔案中，加入 增益集的 主機 檢視的命名空間參考： `CalcHVAs`。 (在 Visual Basic 中為這個命名空間參考`Calc1HVA.CalcHVAs`，除非您已在 Visual Basic 專案中關閉的預設命名空間。)  
  
8.  在**方案總管] 中**，選取方案以及從**專案**功能表中選擇 [**屬性**。 在**方案屬性頁** 對話方塊中，將**單一啟始專案**是這個主機應用程式專案。  
  
9. 在類別或模組檔案中，使用<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>方法，以更新快取。 使用<xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType>方法來取得權杖，集合使用<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>方法來啟動增益集。  
  
     下列程式碼顯示完整的主應用程式。  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  此程式碼會假設管線資料夾結構位於應用程式資料夾。 如果您位於其他地方，變更設定的程式碼行`addInRoot`變數，使變數包含管線目錄結構的路徑。  
  
     程式碼會使用`ChooseCalculator`清單語彙基元，並提示使用者選擇增益集的方法。 `RunCalculator`方法提示使用者提供簡單的數學運算式時，會剖析運算式使用`Parser`類別，並顯示增益集所傳回的結果。  
  
10. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="creating-the-add-in"></a>建立增益集  
 增益集實作增益集的檢視所指定的方法。 此增益集實作`Add`， `Subtract`， `Multiply`，和`Divide`作業並將結果傳回到主應用程式。  
  
#### <a name="to-create-the-add-in"></a>若要建立增益集  
  
1.  加入新的專案，名為`AddInCalcV1`至`CalculatorV1`方案。 它的基礎**類別庫**範本。  
  
2.  在**方案總管 中**，System.AddIn.dll 組件的參考加入專案。  
  
3.  將專案參考加入`Calc1AddInView`專案。 選取該專案的參考，然後在**屬性**，將**複製到本機**至**False**。 在 Visual Basic 使用**參考** 索引標籤**專案屬性**設定**複製到本機**至**False**專案參考。  
  
4.  重新命名類別`AddInCalcV1`。  
  
5.  在類別檔案中，加入的命名空間參考<xref:System.AddIn>與增益集的檢視區段： `CalcAddInViews` (`Calc1AddInView.CalcAddInViews`在 Visual Basic 中)。  
  
6.  套用<xref:System.AddIn.AddInAttribute>屬性`AddInCalcV1`類別，以將類別識別為增益集。  
  
7.  請`AddInCalcV1`類別實作介面代表增益集的檢視： `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator`在 Visual Basic 中)。  
  
8.  實作的成員`ICalculator`藉由傳回適當的計算結果。  
  
     下列程式碼會顯示已完成的增益集。  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. （選擇性） 建置的 Visual Studio 方案。  
  
## <a name="deploying-the-pipeline"></a>部署管線  
 您現在準備建置和增益集區段部署至必要的管線目錄結構。  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>將區段部署至管線  
  
1.  針對每個專案方案中，使用**建置** 索引標籤**專案屬性**(**編譯** 索引標籤，在 Visual Basic 中的) 設定的值**輸出路徑** (**建置輸出路徑**在 Visual Basic 中)。 如果您命名為應用程式資料夾`MyApp`，比方說，您的專案會建置至下列資料夾：  
  
    |專案|路徑|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  如果您決定要在應用程式資料夾以外的位置中放置管線資料夾結構，您必須修改顯示在資料表中的對應路徑。 請參閱中的管線目錄需求的討論[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
2.  建置 Visual Studio 方案。  
  
3.  請檢查以確保組件已複製到正確的目錄，而且沒有額外的複製的組件已安裝不正確的資料夾中的應用程式和管線目錄。  
  
    > [!NOTE]
    >  如果您沒有變更**複製到本機**至**False**如`Calc1AddInView`專案中的參考`AddInCalcV1`專案中，載入器環境問題會造成增益集無法找到。  
  
     如需部署到管線的相關資訊，請參閱[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
## <a name="running-the-host-application"></a>執行主應用程式  
 現在您已經準備好要執行主機及互動 增益集。  
  
#### <a name="to-run-the-host-application"></a>執行主應用程式  
  
1.  在命令提示字元中，移至應用程式目錄和執行主應用程式， `Calc1Host.exe`。  
  
2.  主機會尋找其類型的所有可用增益，並提示您選取的增益集。 輸入**1**唯一可用的增益集。  
  
3.  輸入的方程式計算機，例如**2 + 2**。 必須要有數字和運算子之間的空格。  
  
4.  型別**結束**按**Enter**鍵以關閉應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 啟用主機變更為回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [主控件與增益集之間的逐步解說： 傳遞集合](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [合約、 檢視和配接器](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [管線開發](../../../docs/framework/add-ins/pipeline-development.md)
