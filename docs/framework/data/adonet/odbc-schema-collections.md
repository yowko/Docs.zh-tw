---
title: "ODBC 結構描述集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="86757-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="86757-102">ODBC Schema Collections</span></span>
<span data-ttu-id="86757-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="86757-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="86757-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86757-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="86757-105">Microsoft SQL Server ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="86757-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="86757-106">資料表</span><span class="sxs-lookup"><span data-stu-id="86757-106">Tables</span></span>  
  
-   <span data-ttu-id="86757-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="86757-107">Indexes</span></span>  
  
-   <span data-ttu-id="86757-108">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-108">Columns</span></span>  
  
-   <span data-ttu-id="86757-109">程序</span><span class="sxs-lookup"><span data-stu-id="86757-109">Procedures</span></span>  
  
-   <span data-ttu-id="86757-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="86757-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="86757-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="86757-112">檢視</span><span class="sxs-lookup"><span data-stu-id="86757-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="86757-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="86757-113">Tables and Views</span></span>  
  
|<span data-ttu-id="86757-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-114">ColumnName</span></span>|<span data-ttu-id="86757-115">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-116">TABLE_CAT</span></span>|<span data-ttu-id="86757-117">String</span><span class="sxs-lookup"><span data-stu-id="86757-117">String</span></span>|  
|<span data-ttu-id="86757-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-118">TABLE_SCHEM</span></span>|<span data-ttu-id="86757-119">String</span><span class="sxs-lookup"><span data-stu-id="86757-119">String</span></span>|  
|<span data-ttu-id="86757-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-120">TABLE_NAME</span></span>|<span data-ttu-id="86757-121">String</span><span class="sxs-lookup"><span data-stu-id="86757-121">String</span></span>|  
|<span data-ttu-id="86757-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-122">TABLE_TYPE</span></span>|<span data-ttu-id="86757-123">String</span><span class="sxs-lookup"><span data-stu-id="86757-123">String</span></span>|  
|<span data-ttu-id="86757-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-124">REMARKS</span></span>|<span data-ttu-id="86757-125">String</span><span class="sxs-lookup"><span data-stu-id="86757-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="86757-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="86757-126">Indexes</span></span>  
  
|<span data-ttu-id="86757-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-127">ColumnName</span></span>|<span data-ttu-id="86757-128">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-129">TABLE_CAT</span></span>|<span data-ttu-id="86757-130">String</span><span class="sxs-lookup"><span data-stu-id="86757-130">String</span></span>|  
|<span data-ttu-id="86757-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-131">TABLE_SCHEM</span></span>|<span data-ttu-id="86757-132">String</span><span class="sxs-lookup"><span data-stu-id="86757-132">String</span></span>|  
|<span data-ttu-id="86757-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-133">TABLE_NAME</span></span>|<span data-ttu-id="86757-134">String</span><span class="sxs-lookup"><span data-stu-id="86757-134">String</span></span>|  
|<span data-ttu-id="86757-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="86757-135">NON_UNIQUE</span></span>|<span data-ttu-id="86757-136">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-136">Int16</span></span>|  
|<span data-ttu-id="86757-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="86757-138">String</span><span class="sxs-lookup"><span data-stu-id="86757-138">String</span></span>|  
|<span data-ttu-id="86757-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-139">INDEX_NAME</span></span>|<span data-ttu-id="86757-140">String</span><span class="sxs-lookup"><span data-stu-id="86757-140">String</span></span>|  
|<span data-ttu-id="86757-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-141">TYPE</span></span>|<span data-ttu-id="86757-142">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-142">Int16</span></span>|  
|<span data-ttu-id="86757-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-144">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-144">Int16</span></span>|  
|<span data-ttu-id="86757-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-145">COLUMN_NAME</span></span>|<span data-ttu-id="86757-146">String</span><span class="sxs-lookup"><span data-stu-id="86757-146">String</span></span>|  
|<span data-ttu-id="86757-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="86757-147">ASC_OR_DESC</span></span>|<span data-ttu-id="86757-148">String</span><span class="sxs-lookup"><span data-stu-id="86757-148">String</span></span>|  
|<span data-ttu-id="86757-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="86757-149">CARDINATLITY</span></span>|<span data-ttu-id="86757-150">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-150">Int32</span></span>|  
|<span data-ttu-id="86757-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="86757-151">PAGES</span></span>|<span data-ttu-id="86757-152">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-152">Int32</span></span>|  
|<span data-ttu-id="86757-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="86757-153">FILTER_CONDITION</span></span>|<span data-ttu-id="86757-154">String</span><span class="sxs-lookup"><span data-stu-id="86757-154">String</span></span>|  
|<span data-ttu-id="86757-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="86757-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="86757-156">String</span><span class="sxs-lookup"><span data-stu-id="86757-156">String</span></span>|  
|<span data-ttu-id="86757-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="86757-158">Byte</span><span class="sxs-lookup"><span data-stu-id="86757-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="86757-159">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-159">Columns</span></span>  
  
|<span data-ttu-id="86757-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-160">ColumnName</span></span>|<span data-ttu-id="86757-161">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-162">TABLE_CAT</span></span>|<span data-ttu-id="86757-163">String</span><span class="sxs-lookup"><span data-stu-id="86757-163">String</span></span>|  
|<span data-ttu-id="86757-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-164">TABLE_SCHEM</span></span>|<span data-ttu-id="86757-165">String</span><span class="sxs-lookup"><span data-stu-id="86757-165">String</span></span>|  
|<span data-ttu-id="86757-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-166">TABLE_NAME</span></span>|<span data-ttu-id="86757-167">String</span><span class="sxs-lookup"><span data-stu-id="86757-167">String</span></span>|  
|<span data-ttu-id="86757-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-168">COLUMN_NAME</span></span>|<span data-ttu-id="86757-169">String</span><span class="sxs-lookup"><span data-stu-id="86757-169">String</span></span>|  
|<span data-ttu-id="86757-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-170">DATA_TYPE</span></span>|<span data-ttu-id="86757-171">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-171">Int16</span></span>|  
|<span data-ttu-id="86757-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-172">TYPE_NAME</span></span>|<span data-ttu-id="86757-173">String</span><span class="sxs-lookup"><span data-stu-id="86757-173">String</span></span>|  
|<span data-ttu-id="86757-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="86757-174">COLUMN_SIZE</span></span>|<span data-ttu-id="86757-175">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-175">Int32</span></span>|  
|<span data-ttu-id="86757-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="86757-177">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-177">Int32</span></span>|  
|<span data-ttu-id="86757-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="86757-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="86757-179">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-179">Int16</span></span>|  
|<span data-ttu-id="86757-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="86757-181">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-181">Int16</span></span>|  
|<span data-ttu-id="86757-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-182">NULLABLE</span></span>|<span data-ttu-id="86757-183">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-183">Int16</span></span>|  
|<span data-ttu-id="86757-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-184">REMARKS</span></span>|<span data-ttu-id="86757-185">String</span><span class="sxs-lookup"><span data-stu-id="86757-185">String</span></span>|  
|<span data-ttu-id="86757-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="86757-186">COLUMN_DEF</span></span>|<span data-ttu-id="86757-187">String</span><span class="sxs-lookup"><span data-stu-id="86757-187">String</span></span>|  
|<span data-ttu-id="86757-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="86757-189">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-189">Int16</span></span>|  
|<span data-ttu-id="86757-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="86757-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="86757-191">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-191">Int16</span></span>|  
|<span data-ttu-id="86757-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="86757-193">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-193">Int32</span></span>|  
|<span data-ttu-id="86757-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-195">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-195">Int32</span></span>|  
|<span data-ttu-id="86757-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-196">IS_NULLABLE</span></span>|<span data-ttu-id="86757-197">String</span><span class="sxs-lookup"><span data-stu-id="86757-197">String</span></span>|  
|<span data-ttu-id="86757-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="86757-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="86757-199">String</span><span class="sxs-lookup"><span data-stu-id="86757-199">String</span></span>|  
|<span data-ttu-id="86757-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="86757-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="86757-201">String</span><span class="sxs-lookup"><span data-stu-id="86757-201">String</span></span>|  
|<span data-ttu-id="86757-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="86757-203">Byte</span><span class="sxs-lookup"><span data-stu-id="86757-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="86757-204">程序</span><span class="sxs-lookup"><span data-stu-id="86757-204">Procedures</span></span>  
  
|<span data-ttu-id="86757-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-205">ColumnName</span></span>|<span data-ttu-id="86757-206">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="86757-208">String</span><span class="sxs-lookup"><span data-stu-id="86757-208">String</span></span>|  
|<span data-ttu-id="86757-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="86757-210">String</span><span class="sxs-lookup"><span data-stu-id="86757-210">String</span></span>|  
|<span data-ttu-id="86757-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-212">String</span><span class="sxs-lookup"><span data-stu-id="86757-212">String</span></span>|  
|<span data-ttu-id="86757-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="86757-214">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-214">Int32</span></span>|  
|<span data-ttu-id="86757-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="86757-216">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-216">Int32</span></span>|  
|<span data-ttu-id="86757-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="86757-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="86757-218">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-218">Int32</span></span>|  
|<span data-ttu-id="86757-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-219">REMARKS</span></span>|<span data-ttu-id="86757-220">String</span><span class="sxs-lookup"><span data-stu-id="86757-220">String</span></span>|  
|<span data-ttu-id="86757-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="86757-222">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="86757-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="86757-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-224">ColumnName</span></span>|<span data-ttu-id="86757-225">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="86757-227">String</span><span class="sxs-lookup"><span data-stu-id="86757-227">String</span></span>|  
|<span data-ttu-id="86757-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="86757-229">String</span><span class="sxs-lookup"><span data-stu-id="86757-229">String</span></span>|  
|<span data-ttu-id="86757-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-231">String</span><span class="sxs-lookup"><span data-stu-id="86757-231">String</span></span>|  
|<span data-ttu-id="86757-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-232">COLUMN_NAME</span></span>|<span data-ttu-id="86757-233">String</span><span class="sxs-lookup"><span data-stu-id="86757-233">String</span></span>|  
|<span data-ttu-id="86757-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-234">COLUMN_TYPE</span></span>|<span data-ttu-id="86757-235">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-235">Int16</span></span>|  
|<span data-ttu-id="86757-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-236">DATA_TYPE</span></span>|<span data-ttu-id="86757-237">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-237">Int16</span></span>|  
|<span data-ttu-id="86757-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-238">TYPE_NAME</span></span>|<span data-ttu-id="86757-239">String</span><span class="sxs-lookup"><span data-stu-id="86757-239">String</span></span>|  
|<span data-ttu-id="86757-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="86757-240">COLUMN_SIZE</span></span>|<span data-ttu-id="86757-241">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-241">Int32</span></span>|  
|<span data-ttu-id="86757-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="86757-243">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-243">Int32</span></span>|  
|<span data-ttu-id="86757-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="86757-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="86757-245">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-245">Int16</span></span>|  
|<span data-ttu-id="86757-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="86757-247">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-247">Int16</span></span>|  
|<span data-ttu-id="86757-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-248">NULLABLE</span></span>|<span data-ttu-id="86757-249">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-249">Int16</span></span>|  
|<span data-ttu-id="86757-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-250">REMARKS</span></span>|<span data-ttu-id="86757-251">String</span><span class="sxs-lookup"><span data-stu-id="86757-251">String</span></span>|  
|<span data-ttu-id="86757-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="86757-252">COLUMN_DEF</span></span>|<span data-ttu-id="86757-253">String</span><span class="sxs-lookup"><span data-stu-id="86757-253">String</span></span>|  
|<span data-ttu-id="86757-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="86757-255">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-255">Int16</span></span>|  
|<span data-ttu-id="86757-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="86757-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="86757-257">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-257">Int16</span></span>|  
|<span data-ttu-id="86757-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="86757-259">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-259">Int32</span></span>|  
|<span data-ttu-id="86757-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-261">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-261">Int32</span></span>|  
|<span data-ttu-id="86757-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-262">IS_NULLABLE</span></span>|<span data-ttu-id="86757-263">String</span><span class="sxs-lookup"><span data-stu-id="86757-263">String</span></span>|  
|<span data-ttu-id="86757-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="86757-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="86757-265">String</span><span class="sxs-lookup"><span data-stu-id="86757-265">String</span></span>|  
|<span data-ttu-id="86757-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="86757-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="86757-267">String</span><span class="sxs-lookup"><span data-stu-id="86757-267">String</span></span>|  
|<span data-ttu-id="86757-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="86757-269">Byte</span><span class="sxs-lookup"><span data-stu-id="86757-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="86757-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="86757-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="86757-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-271">ColumnName</span></span>|<span data-ttu-id="86757-272">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="86757-274">String</span><span class="sxs-lookup"><span data-stu-id="86757-274">String</span></span>|  
|<span data-ttu-id="86757-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="86757-276">String</span><span class="sxs-lookup"><span data-stu-id="86757-276">String</span></span>|  
|<span data-ttu-id="86757-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-278">String</span><span class="sxs-lookup"><span data-stu-id="86757-278">String</span></span>|  
|<span data-ttu-id="86757-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-279">COLUMN_NAME</span></span>|<span data-ttu-id="86757-280">String</span><span class="sxs-lookup"><span data-stu-id="86757-280">String</span></span>|  
|<span data-ttu-id="86757-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-281">COLUMN_TYPE</span></span>|<span data-ttu-id="86757-282">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-282">Int16</span></span>|  
|<span data-ttu-id="86757-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-283">DATA_TYPE</span></span>|<span data-ttu-id="86757-284">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-284">Int16</span></span>|  
|<span data-ttu-id="86757-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-285">TYPE_NAME</span></span>|<span data-ttu-id="86757-286">String</span><span class="sxs-lookup"><span data-stu-id="86757-286">String</span></span>|  
|<span data-ttu-id="86757-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="86757-287">COLUMN_SIZE</span></span>|<span data-ttu-id="86757-288">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-288">Int32</span></span>|  
|<span data-ttu-id="86757-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="86757-290">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-290">Int32</span></span>|  
|<span data-ttu-id="86757-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="86757-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="86757-292">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-292">Int16</span></span>|  
|<span data-ttu-id="86757-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="86757-294">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-294">Int16</span></span>|  
|<span data-ttu-id="86757-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-295">NULLABLE</span></span>|<span data-ttu-id="86757-296">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-296">Int16</span></span>|  
|<span data-ttu-id="86757-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-297">REMARKS</span></span>|<span data-ttu-id="86757-298">String</span><span class="sxs-lookup"><span data-stu-id="86757-298">String</span></span>|  
|<span data-ttu-id="86757-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="86757-299">COLUMN_DEF</span></span>|<span data-ttu-id="86757-300">String</span><span class="sxs-lookup"><span data-stu-id="86757-300">String</span></span>|  
|<span data-ttu-id="86757-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="86757-302">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-302">Int16</span></span>|  
|<span data-ttu-id="86757-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="86757-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="86757-304">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-304">Int16</span></span>|  
|<span data-ttu-id="86757-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="86757-306">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-306">Int32</span></span>|  
|<span data-ttu-id="86757-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-308">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-308">Int32</span></span>|  
|<span data-ttu-id="86757-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-309">IS_NULLABLE</span></span>|<span data-ttu-id="86757-310">String</span><span class="sxs-lookup"><span data-stu-id="86757-310">String</span></span>|  
|<span data-ttu-id="86757-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="86757-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="86757-312">String</span><span class="sxs-lookup"><span data-stu-id="86757-312">String</span></span>|  
|<span data-ttu-id="86757-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="86757-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="86757-314">String</span><span class="sxs-lookup"><span data-stu-id="86757-314">String</span></span>|  
|<span data-ttu-id="86757-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="86757-316">Byte</span><span class="sxs-lookup"><span data-stu-id="86757-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="86757-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86757-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="86757-318">Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定的結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="86757-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="86757-319">資料表</span><span class="sxs-lookup"><span data-stu-id="86757-319">Tables</span></span>  
  
-   <span data-ttu-id="86757-320">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-320">Columns</span></span>  
  
-   <span data-ttu-id="86757-321">程序</span><span class="sxs-lookup"><span data-stu-id="86757-321">Procedures</span></span>  
  
-   <span data-ttu-id="86757-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="86757-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="86757-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="86757-324">檢視</span><span class="sxs-lookup"><span data-stu-id="86757-324">Views</span></span>  
  
-   <span data-ttu-id="86757-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="86757-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="86757-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="86757-326">Tables and Views</span></span>  
  
|<span data-ttu-id="86757-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-327">ColumnName</span></span>|<span data-ttu-id="86757-328">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="86757-330">String</span><span class="sxs-lookup"><span data-stu-id="86757-330">String</span></span>|  
|<span data-ttu-id="86757-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-331">TABLE_OWNER</span></span>|<span data-ttu-id="86757-332">String</span><span class="sxs-lookup"><span data-stu-id="86757-332">String</span></span>|  
|<span data-ttu-id="86757-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-333">TABLE_NAME</span></span>|<span data-ttu-id="86757-334">String</span><span class="sxs-lookup"><span data-stu-id="86757-334">String</span></span>|  
|<span data-ttu-id="86757-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-335">TABLE_TYPE</span></span>|<span data-ttu-id="86757-336">String</span><span class="sxs-lookup"><span data-stu-id="86757-336">String</span></span>|  
|<span data-ttu-id="86757-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-337">REMARKS</span></span>|<span data-ttu-id="86757-338">String</span><span class="sxs-lookup"><span data-stu-id="86757-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="86757-339">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-339">Columns</span></span>  
  
|<span data-ttu-id="86757-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-340">ColumnName</span></span>|<span data-ttu-id="86757-341">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="86757-343">String</span><span class="sxs-lookup"><span data-stu-id="86757-343">String</span></span>|  
|<span data-ttu-id="86757-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-344">TABLE_OWNER</span></span>|<span data-ttu-id="86757-345">String</span><span class="sxs-lookup"><span data-stu-id="86757-345">String</span></span>|  
|<span data-ttu-id="86757-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-346">TABLE_NAME</span></span>|<span data-ttu-id="86757-347">String</span><span class="sxs-lookup"><span data-stu-id="86757-347">String</span></span>|  
|<span data-ttu-id="86757-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-348">COLUMN_NAME</span></span>|<span data-ttu-id="86757-349">String</span><span class="sxs-lookup"><span data-stu-id="86757-349">String</span></span>|  
|<span data-ttu-id="86757-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-350">DATA_TYPE</span></span>|<span data-ttu-id="86757-351">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-351">Int16</span></span>|  
|<span data-ttu-id="86757-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-352">TYPE_NAME</span></span>|<span data-ttu-id="86757-353">String</span><span class="sxs-lookup"><span data-stu-id="86757-353">String</span></span>|  
|<span data-ttu-id="86757-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="86757-354">PRECISION</span></span>|<span data-ttu-id="86757-355">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-355">Int32</span></span>|  
|<span data-ttu-id="86757-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-356">LENGTH</span></span>|<span data-ttu-id="86757-357">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-357">Int32</span></span>|  
|<span data-ttu-id="86757-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="86757-358">SCALE</span></span>|<span data-ttu-id="86757-359">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-359">Int16</span></span>|  
|<span data-ttu-id="86757-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-360">RADIX</span></span>|<span data-ttu-id="86757-361">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-361">Int16</span></span>|  
|<span data-ttu-id="86757-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-362">NULLABLE</span></span>|<span data-ttu-id="86757-363">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-363">Int16</span></span>|  
|<span data-ttu-id="86757-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-364">REMARKS</span></span>|<span data-ttu-id="86757-365">String</span><span class="sxs-lookup"><span data-stu-id="86757-365">String</span></span>|  
|<span data-ttu-id="86757-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-367">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="86757-368">程序</span><span class="sxs-lookup"><span data-stu-id="86757-368">Procedures</span></span>  
  
|<span data-ttu-id="86757-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-369">ColumnName</span></span>|<span data-ttu-id="86757-370">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="86757-372">String</span><span class="sxs-lookup"><span data-stu-id="86757-372">String</span></span>|  
|<span data-ttu-id="86757-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="86757-374">String</span><span class="sxs-lookup"><span data-stu-id="86757-374">String</span></span>|  
|<span data-ttu-id="86757-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-376">String</span><span class="sxs-lookup"><span data-stu-id="86757-376">String</span></span>|  
|<span data-ttu-id="86757-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="86757-378">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-378">Int16</span></span>|  
|<span data-ttu-id="86757-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="86757-380">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-380">Int16</span></span>|  
|<span data-ttu-id="86757-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="86757-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="86757-382">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-382">Int16</span></span>|  
|<span data-ttu-id="86757-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-383">REMARKS</span></span>|<span data-ttu-id="86757-384">String</span><span class="sxs-lookup"><span data-stu-id="86757-384">String</span></span>|  
|<span data-ttu-id="86757-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="86757-386">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="86757-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="86757-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-388">ColumnName</span></span>|<span data-ttu-id="86757-389">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="86757-391">String</span><span class="sxs-lookup"><span data-stu-id="86757-391">String</span></span>|  
|<span data-ttu-id="86757-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="86757-393">String</span><span class="sxs-lookup"><span data-stu-id="86757-393">String</span></span>|  
|<span data-ttu-id="86757-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-395">String</span><span class="sxs-lookup"><span data-stu-id="86757-395">String</span></span>|  
|<span data-ttu-id="86757-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-396">COLUMN_NAME</span></span>|<span data-ttu-id="86757-397">String</span><span class="sxs-lookup"><span data-stu-id="86757-397">String</span></span>|  
|<span data-ttu-id="86757-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-398">COLUMN_TYPE</span></span>|<span data-ttu-id="86757-399">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-399">Int16</span></span>|  
|<span data-ttu-id="86757-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-400">DATA_TYPE</span></span>|<span data-ttu-id="86757-401">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-401">Int16</span></span>|  
|<span data-ttu-id="86757-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-402">TYPE_NAME</span></span>|<span data-ttu-id="86757-403">String</span><span class="sxs-lookup"><span data-stu-id="86757-403">String</span></span>|  
|<span data-ttu-id="86757-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="86757-404">PRECISION</span></span>|<span data-ttu-id="86757-405">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-405">Int32</span></span>|  
|<span data-ttu-id="86757-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-406">LENGTH</span></span>|<span data-ttu-id="86757-407">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-407">Int32</span></span>|  
|<span data-ttu-id="86757-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="86757-408">SCALE</span></span>|<span data-ttu-id="86757-409">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-409">Int16</span></span>|  
|<span data-ttu-id="86757-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-410">RADIX</span></span>|<span data-ttu-id="86757-411">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-411">Int16</span></span>|  
|<span data-ttu-id="86757-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-412">NULLABLE</span></span>|<span data-ttu-id="86757-413">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-413">Int16</span></span>|  
|<span data-ttu-id="86757-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-414">REMARKS</span></span>|<span data-ttu-id="86757-415">String</span><span class="sxs-lookup"><span data-stu-id="86757-415">String</span></span>|  
|<span data-ttu-id="86757-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="86757-416">OVERLOAD</span></span>|<span data-ttu-id="86757-417">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-417">Int32</span></span>|  
|<span data-ttu-id="86757-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-419">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="86757-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86757-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="86757-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="86757-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="86757-422">資料表</span><span class="sxs-lookup"><span data-stu-id="86757-422">Tables</span></span>  
  
-   <span data-ttu-id="86757-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="86757-423">Indexes</span></span>  
  
-   <span data-ttu-id="86757-424">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-424">Columns</span></span>  
  
-   <span data-ttu-id="86757-425">程序</span><span class="sxs-lookup"><span data-stu-id="86757-425">Procedures</span></span>  
  
-   <span data-ttu-id="86757-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="86757-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="86757-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="86757-428">檢視</span><span class="sxs-lookup"><span data-stu-id="86757-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="86757-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="86757-429">Tables and Views</span></span>  
  
|<span data-ttu-id="86757-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-430">ColumnName</span></span>|<span data-ttu-id="86757-431">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="86757-433">String</span><span class="sxs-lookup"><span data-stu-id="86757-433">String</span></span>|  
|<span data-ttu-id="86757-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-434">TABLE_OWNER</span></span>|<span data-ttu-id="86757-435">String</span><span class="sxs-lookup"><span data-stu-id="86757-435">String</span></span>|  
|<span data-ttu-id="86757-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-436">TABLE_NAME</span></span>|<span data-ttu-id="86757-437">String</span><span class="sxs-lookup"><span data-stu-id="86757-437">String</span></span>|  
|<span data-ttu-id="86757-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-438">TABLE_TYPE</span></span>|<span data-ttu-id="86757-439">String</span><span class="sxs-lookup"><span data-stu-id="86757-439">String</span></span>|  
|<span data-ttu-id="86757-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-440">REMARKS</span></span>|<span data-ttu-id="86757-441">String</span><span class="sxs-lookup"><span data-stu-id="86757-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="86757-442">資料行</span><span class="sxs-lookup"><span data-stu-id="86757-442">Columns</span></span>  
  
|<span data-ttu-id="86757-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-443">ColumnName</span></span>|<span data-ttu-id="86757-444">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="86757-446">String</span><span class="sxs-lookup"><span data-stu-id="86757-446">String</span></span>|  
|<span data-ttu-id="86757-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-447">TABLE_OWNER</span></span>|<span data-ttu-id="86757-448">String</span><span class="sxs-lookup"><span data-stu-id="86757-448">String</span></span>|  
|<span data-ttu-id="86757-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-449">TABLE_NAME</span></span>|<span data-ttu-id="86757-450">String</span><span class="sxs-lookup"><span data-stu-id="86757-450">String</span></span>|  
|<span data-ttu-id="86757-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-451">COLUMN_NAME</span></span>|<span data-ttu-id="86757-452">String</span><span class="sxs-lookup"><span data-stu-id="86757-452">String</span></span>|  
|<span data-ttu-id="86757-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-453">DATA_TYPE</span></span>|<span data-ttu-id="86757-454">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-454">Int16</span></span>|  
|<span data-ttu-id="86757-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-455">TYPE_NAME</span></span>|<span data-ttu-id="86757-456">String</span><span class="sxs-lookup"><span data-stu-id="86757-456">String</span></span>|  
|<span data-ttu-id="86757-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="86757-457">PRECISION</span></span>|<span data-ttu-id="86757-458">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-458">Int32</span></span>|  
|<span data-ttu-id="86757-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-459">LENGTH</span></span>|<span data-ttu-id="86757-460">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-460">Int32</span></span>|  
|<span data-ttu-id="86757-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="86757-461">SCALE</span></span>|<span data-ttu-id="86757-462">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-462">Int16</span></span>|  
|<span data-ttu-id="86757-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-463">RADIX</span></span>|<span data-ttu-id="86757-464">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-464">Int16</span></span>|  
|<span data-ttu-id="86757-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-465">NULLABLE</span></span>|<span data-ttu-id="86757-466">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-466">Int16</span></span>|  
|<span data-ttu-id="86757-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-467">REMARKS</span></span>|<span data-ttu-id="86757-468">String</span><span class="sxs-lookup"><span data-stu-id="86757-468">String</span></span>|  
|<span data-ttu-id="86757-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-470">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="86757-471">程序</span><span class="sxs-lookup"><span data-stu-id="86757-471">Procedures</span></span>  
  
|<span data-ttu-id="86757-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-472">ColumnName</span></span>|<span data-ttu-id="86757-473">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="86757-475">String</span><span class="sxs-lookup"><span data-stu-id="86757-475">String</span></span>|  
|<span data-ttu-id="86757-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="86757-477">String</span><span class="sxs-lookup"><span data-stu-id="86757-477">String</span></span>|  
|<span data-ttu-id="86757-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-479">String</span><span class="sxs-lookup"><span data-stu-id="86757-479">String</span></span>|  
|<span data-ttu-id="86757-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="86757-481">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-481">Int16</span></span>|  
|<span data-ttu-id="86757-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="86757-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="86757-483">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-483">Int16</span></span>|  
|<span data-ttu-id="86757-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="86757-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="86757-485">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-485">Int16</span></span>|  
|<span data-ttu-id="86757-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-486">REMARKS</span></span>|<span data-ttu-id="86757-487">String</span><span class="sxs-lookup"><span data-stu-id="86757-487">String</span></span>|  
|<span data-ttu-id="86757-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="86757-489">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="86757-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="86757-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="86757-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-491">ColumnName</span></span>|<span data-ttu-id="86757-492">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="86757-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="86757-494">String</span><span class="sxs-lookup"><span data-stu-id="86757-494">String</span></span>|  
|<span data-ttu-id="86757-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="86757-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="86757-496">String</span><span class="sxs-lookup"><span data-stu-id="86757-496">String</span></span>|  
|<span data-ttu-id="86757-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-498">String</span><span class="sxs-lookup"><span data-stu-id="86757-498">String</span></span>|  
|<span data-ttu-id="86757-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-499">COLUMN_NAME</span></span>|<span data-ttu-id="86757-500">String</span><span class="sxs-lookup"><span data-stu-id="86757-500">String</span></span>|  
|<span data-ttu-id="86757-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-501">COLUMN_TYPE</span></span>|<span data-ttu-id="86757-502">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-502">Int16</span></span>|  
|<span data-ttu-id="86757-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-503">DATA_TYPE</span></span>|<span data-ttu-id="86757-504">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-504">Int16</span></span>|  
|<span data-ttu-id="86757-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-505">TYPE_NAME</span></span>|<span data-ttu-id="86757-506">String</span><span class="sxs-lookup"><span data-stu-id="86757-506">String</span></span>|  
|<span data-ttu-id="86757-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="86757-507">PRECISION</span></span>|<span data-ttu-id="86757-508">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-508">Int32</span></span>|  
|<span data-ttu-id="86757-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-509">LENGTH</span></span>|<span data-ttu-id="86757-510">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-510">Int32</span></span>|  
|<span data-ttu-id="86757-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="86757-511">SCALE</span></span>|<span data-ttu-id="86757-512">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-512">Int16</span></span>|  
|<span data-ttu-id="86757-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-513">RADIX</span></span>|<span data-ttu-id="86757-514">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-514">Int16</span></span>|  
|<span data-ttu-id="86757-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-515">NULLABLE</span></span>|<span data-ttu-id="86757-516">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-516">Int16</span></span>|  
|<span data-ttu-id="86757-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-517">REMARKS</span></span>|<span data-ttu-id="86757-518">String</span><span class="sxs-lookup"><span data-stu-id="86757-518">String</span></span>|  
|<span data-ttu-id="86757-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="86757-519">OVERLOAD</span></span>|<span data-ttu-id="86757-520">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-520">Int32</span></span>|  
|<span data-ttu-id="86757-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-522">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="86757-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="86757-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="86757-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="86757-524">ColumnName</span></span>|<span data-ttu-id="86757-525">DataType</span><span class="sxs-lookup"><span data-stu-id="86757-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="86757-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="86757-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="86757-527">String</span><span class="sxs-lookup"><span data-stu-id="86757-527">String</span></span>|  
|<span data-ttu-id="86757-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="86757-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="86757-529">String</span><span class="sxs-lookup"><span data-stu-id="86757-529">String</span></span>|  
|<span data-ttu-id="86757-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="86757-531">String</span><span class="sxs-lookup"><span data-stu-id="86757-531">String</span></span>|  
|<span data-ttu-id="86757-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-532">COLUMN_NAME</span></span>|<span data-ttu-id="86757-533">String</span><span class="sxs-lookup"><span data-stu-id="86757-533">String</span></span>|  
|<span data-ttu-id="86757-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-534">COLUMN_TYPE</span></span>|<span data-ttu-id="86757-535">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-535">Int16</span></span>|  
|<span data-ttu-id="86757-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-536">DATA_TYPE</span></span>|<span data-ttu-id="86757-537">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-537">Int16</span></span>|  
|<span data-ttu-id="86757-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="86757-538">TYPE_NAME</span></span>|<span data-ttu-id="86757-539">String</span><span class="sxs-lookup"><span data-stu-id="86757-539">String</span></span>|  
|<span data-ttu-id="86757-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="86757-540">COLUMN_SIZE</span></span>|<span data-ttu-id="86757-541">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-541">Int32</span></span>|  
|<span data-ttu-id="86757-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="86757-543">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-543">Int32</span></span>|  
|<span data-ttu-id="86757-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="86757-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="86757-545">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-545">Int16</span></span>|  
|<span data-ttu-id="86757-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="86757-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="86757-547">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-547">Int16</span></span>|  
|<span data-ttu-id="86757-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-548">NULLABLE</span></span>|<span data-ttu-id="86757-549">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-549">Int16</span></span>|  
|<span data-ttu-id="86757-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="86757-550">REMARKS</span></span>|<span data-ttu-id="86757-551">String</span><span class="sxs-lookup"><span data-stu-id="86757-551">String</span></span>|  
|<span data-ttu-id="86757-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="86757-552">COLUMN_DEF</span></span>|<span data-ttu-id="86757-553">String</span><span class="sxs-lookup"><span data-stu-id="86757-553">String</span></span>|  
|<span data-ttu-id="86757-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="86757-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="86757-555">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-555">Int16</span></span>|  
|<span data-ttu-id="86757-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="86757-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="86757-557">Int16</span><span class="sxs-lookup"><span data-stu-id="86757-557">Int16</span></span>|  
|<span data-ttu-id="86757-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="86757-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="86757-559">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-559">Int32</span></span>|  
|<span data-ttu-id="86757-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="86757-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="86757-561">Int32</span><span class="sxs-lookup"><span data-stu-id="86757-561">Int32</span></span>|  
|<span data-ttu-id="86757-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="86757-562">IS_NULLABLE</span></span>|<span data-ttu-id="86757-563">字串</span><span class="sxs-lookup"><span data-stu-id="86757-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86757-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86757-564">See Also</span></span>  
 [<span data-ttu-id="86757-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="86757-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
