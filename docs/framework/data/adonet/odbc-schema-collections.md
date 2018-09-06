---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877527"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="47633-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="47633-102">ODBC Schema Collections</span></span>
<span data-ttu-id="47633-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="47633-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="47633-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="47633-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="47633-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="47633-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="47633-106">資料表</span><span class="sxs-lookup"><span data-stu-id="47633-106">Tables</span></span>  
  
-   <span data-ttu-id="47633-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="47633-107">Indexes</span></span>  
  
-   <span data-ttu-id="47633-108">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-108">Columns</span></span>  
  
-   <span data-ttu-id="47633-109">程序</span><span class="sxs-lookup"><span data-stu-id="47633-109">Procedures</span></span>  
  
-   <span data-ttu-id="47633-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="47633-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="47633-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="47633-112">檢視</span><span class="sxs-lookup"><span data-stu-id="47633-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="47633-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="47633-113">Tables and Views</span></span>  
  
|<span data-ttu-id="47633-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-114">ColumnName</span></span>|<span data-ttu-id="47633-115">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-116">TABLE_CAT</span></span>|<span data-ttu-id="47633-117">String</span><span class="sxs-lookup"><span data-stu-id="47633-117">String</span></span>|  
|<span data-ttu-id="47633-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-118">TABLE_SCHEM</span></span>|<span data-ttu-id="47633-119">String</span><span class="sxs-lookup"><span data-stu-id="47633-119">String</span></span>|  
|<span data-ttu-id="47633-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-120">TABLE_NAME</span></span>|<span data-ttu-id="47633-121">String</span><span class="sxs-lookup"><span data-stu-id="47633-121">String</span></span>|  
|<span data-ttu-id="47633-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-122">TABLE_TYPE</span></span>|<span data-ttu-id="47633-123">String</span><span class="sxs-lookup"><span data-stu-id="47633-123">String</span></span>|  
|<span data-ttu-id="47633-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-124">REMARKS</span></span>|<span data-ttu-id="47633-125">String</span><span class="sxs-lookup"><span data-stu-id="47633-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="47633-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="47633-126">Indexes</span></span>  
  
|<span data-ttu-id="47633-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-127">ColumnName</span></span>|<span data-ttu-id="47633-128">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-129">TABLE_CAT</span></span>|<span data-ttu-id="47633-130">String</span><span class="sxs-lookup"><span data-stu-id="47633-130">String</span></span>|  
|<span data-ttu-id="47633-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-131">TABLE_SCHEM</span></span>|<span data-ttu-id="47633-132">String</span><span class="sxs-lookup"><span data-stu-id="47633-132">String</span></span>|  
|<span data-ttu-id="47633-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-133">TABLE_NAME</span></span>|<span data-ttu-id="47633-134">String</span><span class="sxs-lookup"><span data-stu-id="47633-134">String</span></span>|  
|<span data-ttu-id="47633-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="47633-135">NON_UNIQUE</span></span>|<span data-ttu-id="47633-136">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-136">Int16</span></span>|  
|<span data-ttu-id="47633-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="47633-138">String</span><span class="sxs-lookup"><span data-stu-id="47633-138">String</span></span>|  
|<span data-ttu-id="47633-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-139">INDEX_NAME</span></span>|<span data-ttu-id="47633-140">String</span><span class="sxs-lookup"><span data-stu-id="47633-140">String</span></span>|  
|<span data-ttu-id="47633-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-141">TYPE</span></span>|<span data-ttu-id="47633-142">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-142">Int16</span></span>|  
|<span data-ttu-id="47633-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-144">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-144">Int16</span></span>|  
|<span data-ttu-id="47633-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-145">COLUMN_NAME</span></span>|<span data-ttu-id="47633-146">String</span><span class="sxs-lookup"><span data-stu-id="47633-146">String</span></span>|  
|<span data-ttu-id="47633-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="47633-147">ASC_OR_DESC</span></span>|<span data-ttu-id="47633-148">String</span><span class="sxs-lookup"><span data-stu-id="47633-148">String</span></span>|  
|<span data-ttu-id="47633-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="47633-149">CARDINATLITY</span></span>|<span data-ttu-id="47633-150">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-150">Int32</span></span>|  
|<span data-ttu-id="47633-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="47633-151">PAGES</span></span>|<span data-ttu-id="47633-152">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-152">Int32</span></span>|  
|<span data-ttu-id="47633-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="47633-153">FILTER_CONDITION</span></span>|<span data-ttu-id="47633-154">String</span><span class="sxs-lookup"><span data-stu-id="47633-154">String</span></span>|  
|<span data-ttu-id="47633-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="47633-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="47633-156">String</span><span class="sxs-lookup"><span data-stu-id="47633-156">String</span></span>|  
|<span data-ttu-id="47633-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="47633-158">Byte</span><span class="sxs-lookup"><span data-stu-id="47633-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="47633-159">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-159">Columns</span></span>  
  
|<span data-ttu-id="47633-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-160">ColumnName</span></span>|<span data-ttu-id="47633-161">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-162">TABLE_CAT</span></span>|<span data-ttu-id="47633-163">String</span><span class="sxs-lookup"><span data-stu-id="47633-163">String</span></span>|  
|<span data-ttu-id="47633-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-164">TABLE_SCHEM</span></span>|<span data-ttu-id="47633-165">String</span><span class="sxs-lookup"><span data-stu-id="47633-165">String</span></span>|  
|<span data-ttu-id="47633-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-166">TABLE_NAME</span></span>|<span data-ttu-id="47633-167">String</span><span class="sxs-lookup"><span data-stu-id="47633-167">String</span></span>|  
|<span data-ttu-id="47633-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-168">COLUMN_NAME</span></span>|<span data-ttu-id="47633-169">String</span><span class="sxs-lookup"><span data-stu-id="47633-169">String</span></span>|  
|<span data-ttu-id="47633-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-170">DATA_TYPE</span></span>|<span data-ttu-id="47633-171">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-171">Int16</span></span>|  
|<span data-ttu-id="47633-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-172">TYPE_NAME</span></span>|<span data-ttu-id="47633-173">String</span><span class="sxs-lookup"><span data-stu-id="47633-173">String</span></span>|  
|<span data-ttu-id="47633-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="47633-174">COLUMN_SIZE</span></span>|<span data-ttu-id="47633-175">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-175">Int32</span></span>|  
|<span data-ttu-id="47633-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="47633-177">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-177">Int32</span></span>|  
|<span data-ttu-id="47633-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="47633-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="47633-179">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-179">Int16</span></span>|  
|<span data-ttu-id="47633-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="47633-181">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-181">Int16</span></span>|  
|<span data-ttu-id="47633-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-182">NULLABLE</span></span>|<span data-ttu-id="47633-183">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-183">Int16</span></span>|  
|<span data-ttu-id="47633-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-184">REMARKS</span></span>|<span data-ttu-id="47633-185">String</span><span class="sxs-lookup"><span data-stu-id="47633-185">String</span></span>|  
|<span data-ttu-id="47633-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="47633-186">COLUMN_DEF</span></span>|<span data-ttu-id="47633-187">String</span><span class="sxs-lookup"><span data-stu-id="47633-187">String</span></span>|  
|<span data-ttu-id="47633-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="47633-189">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-189">Int16</span></span>|  
|<span data-ttu-id="47633-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="47633-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="47633-191">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-191">Int16</span></span>|  
|<span data-ttu-id="47633-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="47633-193">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-193">Int32</span></span>|  
|<span data-ttu-id="47633-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-195">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-195">Int32</span></span>|  
|<span data-ttu-id="47633-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-196">IS_NULLABLE</span></span>|<span data-ttu-id="47633-197">String</span><span class="sxs-lookup"><span data-stu-id="47633-197">String</span></span>|  
|<span data-ttu-id="47633-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="47633-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="47633-199">String</span><span class="sxs-lookup"><span data-stu-id="47633-199">String</span></span>|  
|<span data-ttu-id="47633-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="47633-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="47633-201">String</span><span class="sxs-lookup"><span data-stu-id="47633-201">String</span></span>|  
|<span data-ttu-id="47633-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="47633-203">Byte</span><span class="sxs-lookup"><span data-stu-id="47633-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="47633-204">程序</span><span class="sxs-lookup"><span data-stu-id="47633-204">Procedures</span></span>  
  
|<span data-ttu-id="47633-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-205">ColumnName</span></span>|<span data-ttu-id="47633-206">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="47633-208">String</span><span class="sxs-lookup"><span data-stu-id="47633-208">String</span></span>|  
|<span data-ttu-id="47633-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="47633-210">String</span><span class="sxs-lookup"><span data-stu-id="47633-210">String</span></span>|  
|<span data-ttu-id="47633-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-212">String</span><span class="sxs-lookup"><span data-stu-id="47633-212">String</span></span>|  
|<span data-ttu-id="47633-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="47633-214">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-214">Int32</span></span>|  
|<span data-ttu-id="47633-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="47633-216">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-216">Int32</span></span>|  
|<span data-ttu-id="47633-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="47633-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="47633-218">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-218">Int32</span></span>|  
|<span data-ttu-id="47633-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-219">REMARKS</span></span>|<span data-ttu-id="47633-220">String</span><span class="sxs-lookup"><span data-stu-id="47633-220">String</span></span>|  
|<span data-ttu-id="47633-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="47633-222">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="47633-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="47633-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-224">ColumnName</span></span>|<span data-ttu-id="47633-225">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="47633-227">String</span><span class="sxs-lookup"><span data-stu-id="47633-227">String</span></span>|  
|<span data-ttu-id="47633-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="47633-229">String</span><span class="sxs-lookup"><span data-stu-id="47633-229">String</span></span>|  
|<span data-ttu-id="47633-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-231">String</span><span class="sxs-lookup"><span data-stu-id="47633-231">String</span></span>|  
|<span data-ttu-id="47633-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-232">COLUMN_NAME</span></span>|<span data-ttu-id="47633-233">String</span><span class="sxs-lookup"><span data-stu-id="47633-233">String</span></span>|  
|<span data-ttu-id="47633-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-234">COLUMN_TYPE</span></span>|<span data-ttu-id="47633-235">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-235">Int16</span></span>|  
|<span data-ttu-id="47633-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-236">DATA_TYPE</span></span>|<span data-ttu-id="47633-237">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-237">Int16</span></span>|  
|<span data-ttu-id="47633-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-238">TYPE_NAME</span></span>|<span data-ttu-id="47633-239">String</span><span class="sxs-lookup"><span data-stu-id="47633-239">String</span></span>|  
|<span data-ttu-id="47633-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="47633-240">COLUMN_SIZE</span></span>|<span data-ttu-id="47633-241">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-241">Int32</span></span>|  
|<span data-ttu-id="47633-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="47633-243">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-243">Int32</span></span>|  
|<span data-ttu-id="47633-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="47633-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="47633-245">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-245">Int16</span></span>|  
|<span data-ttu-id="47633-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="47633-247">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-247">Int16</span></span>|  
|<span data-ttu-id="47633-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-248">NULLABLE</span></span>|<span data-ttu-id="47633-249">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-249">Int16</span></span>|  
|<span data-ttu-id="47633-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-250">REMARKS</span></span>|<span data-ttu-id="47633-251">String</span><span class="sxs-lookup"><span data-stu-id="47633-251">String</span></span>|  
|<span data-ttu-id="47633-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="47633-252">COLUMN_DEF</span></span>|<span data-ttu-id="47633-253">String</span><span class="sxs-lookup"><span data-stu-id="47633-253">String</span></span>|  
|<span data-ttu-id="47633-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="47633-255">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-255">Int16</span></span>|  
|<span data-ttu-id="47633-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="47633-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="47633-257">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-257">Int16</span></span>|  
|<span data-ttu-id="47633-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="47633-259">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-259">Int32</span></span>|  
|<span data-ttu-id="47633-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-261">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-261">Int32</span></span>|  
|<span data-ttu-id="47633-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-262">IS_NULLABLE</span></span>|<span data-ttu-id="47633-263">String</span><span class="sxs-lookup"><span data-stu-id="47633-263">String</span></span>|  
|<span data-ttu-id="47633-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="47633-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="47633-265">String</span><span class="sxs-lookup"><span data-stu-id="47633-265">String</span></span>|  
|<span data-ttu-id="47633-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="47633-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="47633-267">String</span><span class="sxs-lookup"><span data-stu-id="47633-267">String</span></span>|  
|<span data-ttu-id="47633-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="47633-269">Byte</span><span class="sxs-lookup"><span data-stu-id="47633-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="47633-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="47633-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="47633-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-271">ColumnName</span></span>|<span data-ttu-id="47633-272">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="47633-274">String</span><span class="sxs-lookup"><span data-stu-id="47633-274">String</span></span>|  
|<span data-ttu-id="47633-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="47633-276">String</span><span class="sxs-lookup"><span data-stu-id="47633-276">String</span></span>|  
|<span data-ttu-id="47633-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-278">String</span><span class="sxs-lookup"><span data-stu-id="47633-278">String</span></span>|  
|<span data-ttu-id="47633-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-279">COLUMN_NAME</span></span>|<span data-ttu-id="47633-280">String</span><span class="sxs-lookup"><span data-stu-id="47633-280">String</span></span>|  
|<span data-ttu-id="47633-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-281">COLUMN_TYPE</span></span>|<span data-ttu-id="47633-282">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-282">Int16</span></span>|  
|<span data-ttu-id="47633-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-283">DATA_TYPE</span></span>|<span data-ttu-id="47633-284">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-284">Int16</span></span>|  
|<span data-ttu-id="47633-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-285">TYPE_NAME</span></span>|<span data-ttu-id="47633-286">String</span><span class="sxs-lookup"><span data-stu-id="47633-286">String</span></span>|  
|<span data-ttu-id="47633-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="47633-287">COLUMN_SIZE</span></span>|<span data-ttu-id="47633-288">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-288">Int32</span></span>|  
|<span data-ttu-id="47633-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="47633-290">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-290">Int32</span></span>|  
|<span data-ttu-id="47633-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="47633-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="47633-292">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-292">Int16</span></span>|  
|<span data-ttu-id="47633-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="47633-294">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-294">Int16</span></span>|  
|<span data-ttu-id="47633-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-295">NULLABLE</span></span>|<span data-ttu-id="47633-296">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-296">Int16</span></span>|  
|<span data-ttu-id="47633-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-297">REMARKS</span></span>|<span data-ttu-id="47633-298">String</span><span class="sxs-lookup"><span data-stu-id="47633-298">String</span></span>|  
|<span data-ttu-id="47633-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="47633-299">COLUMN_DEF</span></span>|<span data-ttu-id="47633-300">String</span><span class="sxs-lookup"><span data-stu-id="47633-300">String</span></span>|  
|<span data-ttu-id="47633-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="47633-302">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-302">Int16</span></span>|  
|<span data-ttu-id="47633-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="47633-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="47633-304">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-304">Int16</span></span>|  
|<span data-ttu-id="47633-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="47633-306">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-306">Int32</span></span>|  
|<span data-ttu-id="47633-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-308">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-308">Int32</span></span>|  
|<span data-ttu-id="47633-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-309">IS_NULLABLE</span></span>|<span data-ttu-id="47633-310">String</span><span class="sxs-lookup"><span data-stu-id="47633-310">String</span></span>|  
|<span data-ttu-id="47633-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="47633-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="47633-312">String</span><span class="sxs-lookup"><span data-stu-id="47633-312">String</span></span>|  
|<span data-ttu-id="47633-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="47633-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="47633-314">String</span><span class="sxs-lookup"><span data-stu-id="47633-314">String</span></span>|  
|<span data-ttu-id="47633-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="47633-316">Byte</span><span class="sxs-lookup"><span data-stu-id="47633-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="47633-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="47633-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="47633-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="47633-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="47633-319">資料表</span><span class="sxs-lookup"><span data-stu-id="47633-319">Tables</span></span>  
  
-   <span data-ttu-id="47633-320">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-320">Columns</span></span>  
  
-   <span data-ttu-id="47633-321">程序</span><span class="sxs-lookup"><span data-stu-id="47633-321">Procedures</span></span>  
  
-   <span data-ttu-id="47633-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="47633-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="47633-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="47633-324">檢視</span><span class="sxs-lookup"><span data-stu-id="47633-324">Views</span></span>  
  
-   <span data-ttu-id="47633-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="47633-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="47633-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="47633-326">Tables and Views</span></span>  
  
|<span data-ttu-id="47633-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-327">ColumnName</span></span>|<span data-ttu-id="47633-328">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="47633-330">String</span><span class="sxs-lookup"><span data-stu-id="47633-330">String</span></span>|  
|<span data-ttu-id="47633-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-331">TABLE_OWNER</span></span>|<span data-ttu-id="47633-332">String</span><span class="sxs-lookup"><span data-stu-id="47633-332">String</span></span>|  
|<span data-ttu-id="47633-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-333">TABLE_NAME</span></span>|<span data-ttu-id="47633-334">String</span><span class="sxs-lookup"><span data-stu-id="47633-334">String</span></span>|  
|<span data-ttu-id="47633-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-335">TABLE_TYPE</span></span>|<span data-ttu-id="47633-336">String</span><span class="sxs-lookup"><span data-stu-id="47633-336">String</span></span>|  
|<span data-ttu-id="47633-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-337">REMARKS</span></span>|<span data-ttu-id="47633-338">String</span><span class="sxs-lookup"><span data-stu-id="47633-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="47633-339">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-339">Columns</span></span>  
  
|<span data-ttu-id="47633-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-340">ColumnName</span></span>|<span data-ttu-id="47633-341">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="47633-343">String</span><span class="sxs-lookup"><span data-stu-id="47633-343">String</span></span>|  
|<span data-ttu-id="47633-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-344">TABLE_OWNER</span></span>|<span data-ttu-id="47633-345">String</span><span class="sxs-lookup"><span data-stu-id="47633-345">String</span></span>|  
|<span data-ttu-id="47633-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-346">TABLE_NAME</span></span>|<span data-ttu-id="47633-347">String</span><span class="sxs-lookup"><span data-stu-id="47633-347">String</span></span>|  
|<span data-ttu-id="47633-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-348">COLUMN_NAME</span></span>|<span data-ttu-id="47633-349">String</span><span class="sxs-lookup"><span data-stu-id="47633-349">String</span></span>|  
|<span data-ttu-id="47633-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-350">DATA_TYPE</span></span>|<span data-ttu-id="47633-351">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-351">Int16</span></span>|  
|<span data-ttu-id="47633-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-352">TYPE_NAME</span></span>|<span data-ttu-id="47633-353">String</span><span class="sxs-lookup"><span data-stu-id="47633-353">String</span></span>|  
|<span data-ttu-id="47633-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="47633-354">PRECISION</span></span>|<span data-ttu-id="47633-355">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-355">Int32</span></span>|  
|<span data-ttu-id="47633-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-356">LENGTH</span></span>|<span data-ttu-id="47633-357">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-357">Int32</span></span>|  
|<span data-ttu-id="47633-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="47633-358">SCALE</span></span>|<span data-ttu-id="47633-359">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-359">Int16</span></span>|  
|<span data-ttu-id="47633-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-360">RADIX</span></span>|<span data-ttu-id="47633-361">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-361">Int16</span></span>|  
|<span data-ttu-id="47633-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-362">NULLABLE</span></span>|<span data-ttu-id="47633-363">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-363">Int16</span></span>|  
|<span data-ttu-id="47633-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-364">REMARKS</span></span>|<span data-ttu-id="47633-365">String</span><span class="sxs-lookup"><span data-stu-id="47633-365">String</span></span>|  
|<span data-ttu-id="47633-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-367">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="47633-368">程序</span><span class="sxs-lookup"><span data-stu-id="47633-368">Procedures</span></span>  
  
|<span data-ttu-id="47633-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-369">ColumnName</span></span>|<span data-ttu-id="47633-370">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="47633-372">String</span><span class="sxs-lookup"><span data-stu-id="47633-372">String</span></span>|  
|<span data-ttu-id="47633-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="47633-374">String</span><span class="sxs-lookup"><span data-stu-id="47633-374">String</span></span>|  
|<span data-ttu-id="47633-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-376">String</span><span class="sxs-lookup"><span data-stu-id="47633-376">String</span></span>|  
|<span data-ttu-id="47633-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="47633-378">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-378">Int16</span></span>|  
|<span data-ttu-id="47633-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="47633-380">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-380">Int16</span></span>|  
|<span data-ttu-id="47633-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="47633-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="47633-382">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-382">Int16</span></span>|  
|<span data-ttu-id="47633-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-383">REMARKS</span></span>|<span data-ttu-id="47633-384">String</span><span class="sxs-lookup"><span data-stu-id="47633-384">String</span></span>|  
|<span data-ttu-id="47633-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="47633-386">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="47633-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="47633-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-388">ColumnName</span></span>|<span data-ttu-id="47633-389">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="47633-391">String</span><span class="sxs-lookup"><span data-stu-id="47633-391">String</span></span>|  
|<span data-ttu-id="47633-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="47633-393">String</span><span class="sxs-lookup"><span data-stu-id="47633-393">String</span></span>|  
|<span data-ttu-id="47633-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-395">String</span><span class="sxs-lookup"><span data-stu-id="47633-395">String</span></span>|  
|<span data-ttu-id="47633-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-396">COLUMN_NAME</span></span>|<span data-ttu-id="47633-397">String</span><span class="sxs-lookup"><span data-stu-id="47633-397">String</span></span>|  
|<span data-ttu-id="47633-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-398">COLUMN_TYPE</span></span>|<span data-ttu-id="47633-399">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-399">Int16</span></span>|  
|<span data-ttu-id="47633-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-400">DATA_TYPE</span></span>|<span data-ttu-id="47633-401">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-401">Int16</span></span>|  
|<span data-ttu-id="47633-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-402">TYPE_NAME</span></span>|<span data-ttu-id="47633-403">String</span><span class="sxs-lookup"><span data-stu-id="47633-403">String</span></span>|  
|<span data-ttu-id="47633-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="47633-404">PRECISION</span></span>|<span data-ttu-id="47633-405">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-405">Int32</span></span>|  
|<span data-ttu-id="47633-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-406">LENGTH</span></span>|<span data-ttu-id="47633-407">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-407">Int32</span></span>|  
|<span data-ttu-id="47633-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="47633-408">SCALE</span></span>|<span data-ttu-id="47633-409">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-409">Int16</span></span>|  
|<span data-ttu-id="47633-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-410">RADIX</span></span>|<span data-ttu-id="47633-411">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-411">Int16</span></span>|  
|<span data-ttu-id="47633-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-412">NULLABLE</span></span>|<span data-ttu-id="47633-413">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-413">Int16</span></span>|  
|<span data-ttu-id="47633-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-414">REMARKS</span></span>|<span data-ttu-id="47633-415">String</span><span class="sxs-lookup"><span data-stu-id="47633-415">String</span></span>|  
|<span data-ttu-id="47633-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="47633-416">OVERLOAD</span></span>|<span data-ttu-id="47633-417">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-417">Int32</span></span>|  
|<span data-ttu-id="47633-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-419">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="47633-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="47633-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="47633-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="47633-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="47633-422">資料表</span><span class="sxs-lookup"><span data-stu-id="47633-422">Tables</span></span>  
  
-   <span data-ttu-id="47633-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="47633-423">Indexes</span></span>  
  
-   <span data-ttu-id="47633-424">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-424">Columns</span></span>  
  
-   <span data-ttu-id="47633-425">程序</span><span class="sxs-lookup"><span data-stu-id="47633-425">Procedures</span></span>  
  
-   <span data-ttu-id="47633-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="47633-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="47633-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="47633-428">檢視</span><span class="sxs-lookup"><span data-stu-id="47633-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="47633-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="47633-429">Tables and Views</span></span>  
  
|<span data-ttu-id="47633-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-430">ColumnName</span></span>|<span data-ttu-id="47633-431">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="47633-433">String</span><span class="sxs-lookup"><span data-stu-id="47633-433">String</span></span>|  
|<span data-ttu-id="47633-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-434">TABLE_OWNER</span></span>|<span data-ttu-id="47633-435">String</span><span class="sxs-lookup"><span data-stu-id="47633-435">String</span></span>|  
|<span data-ttu-id="47633-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-436">TABLE_NAME</span></span>|<span data-ttu-id="47633-437">String</span><span class="sxs-lookup"><span data-stu-id="47633-437">String</span></span>|  
|<span data-ttu-id="47633-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-438">TABLE_TYPE</span></span>|<span data-ttu-id="47633-439">String</span><span class="sxs-lookup"><span data-stu-id="47633-439">String</span></span>|  
|<span data-ttu-id="47633-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-440">REMARKS</span></span>|<span data-ttu-id="47633-441">String</span><span class="sxs-lookup"><span data-stu-id="47633-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="47633-442">資料行</span><span class="sxs-lookup"><span data-stu-id="47633-442">Columns</span></span>  
  
|<span data-ttu-id="47633-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-443">ColumnName</span></span>|<span data-ttu-id="47633-444">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="47633-446">String</span><span class="sxs-lookup"><span data-stu-id="47633-446">String</span></span>|  
|<span data-ttu-id="47633-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-447">TABLE_OWNER</span></span>|<span data-ttu-id="47633-448">String</span><span class="sxs-lookup"><span data-stu-id="47633-448">String</span></span>|  
|<span data-ttu-id="47633-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-449">TABLE_NAME</span></span>|<span data-ttu-id="47633-450">String</span><span class="sxs-lookup"><span data-stu-id="47633-450">String</span></span>|  
|<span data-ttu-id="47633-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-451">COLUMN_NAME</span></span>|<span data-ttu-id="47633-452">String</span><span class="sxs-lookup"><span data-stu-id="47633-452">String</span></span>|  
|<span data-ttu-id="47633-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-453">DATA_TYPE</span></span>|<span data-ttu-id="47633-454">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-454">Int16</span></span>|  
|<span data-ttu-id="47633-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-455">TYPE_NAME</span></span>|<span data-ttu-id="47633-456">String</span><span class="sxs-lookup"><span data-stu-id="47633-456">String</span></span>|  
|<span data-ttu-id="47633-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="47633-457">PRECISION</span></span>|<span data-ttu-id="47633-458">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-458">Int32</span></span>|  
|<span data-ttu-id="47633-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-459">LENGTH</span></span>|<span data-ttu-id="47633-460">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-460">Int32</span></span>|  
|<span data-ttu-id="47633-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="47633-461">SCALE</span></span>|<span data-ttu-id="47633-462">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-462">Int16</span></span>|  
|<span data-ttu-id="47633-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-463">RADIX</span></span>|<span data-ttu-id="47633-464">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-464">Int16</span></span>|  
|<span data-ttu-id="47633-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-465">NULLABLE</span></span>|<span data-ttu-id="47633-466">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-466">Int16</span></span>|  
|<span data-ttu-id="47633-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-467">REMARKS</span></span>|<span data-ttu-id="47633-468">String</span><span class="sxs-lookup"><span data-stu-id="47633-468">String</span></span>|  
|<span data-ttu-id="47633-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-470">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="47633-471">程序</span><span class="sxs-lookup"><span data-stu-id="47633-471">Procedures</span></span>  
  
|<span data-ttu-id="47633-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-472">ColumnName</span></span>|<span data-ttu-id="47633-473">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="47633-475">String</span><span class="sxs-lookup"><span data-stu-id="47633-475">String</span></span>|  
|<span data-ttu-id="47633-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="47633-477">String</span><span class="sxs-lookup"><span data-stu-id="47633-477">String</span></span>|  
|<span data-ttu-id="47633-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-479">String</span><span class="sxs-lookup"><span data-stu-id="47633-479">String</span></span>|  
|<span data-ttu-id="47633-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="47633-481">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-481">Int16</span></span>|  
|<span data-ttu-id="47633-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="47633-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="47633-483">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-483">Int16</span></span>|  
|<span data-ttu-id="47633-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="47633-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="47633-485">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-485">Int16</span></span>|  
|<span data-ttu-id="47633-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-486">REMARKS</span></span>|<span data-ttu-id="47633-487">String</span><span class="sxs-lookup"><span data-stu-id="47633-487">String</span></span>|  
|<span data-ttu-id="47633-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="47633-489">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="47633-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="47633-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="47633-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-491">ColumnName</span></span>|<span data-ttu-id="47633-492">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="47633-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="47633-494">String</span><span class="sxs-lookup"><span data-stu-id="47633-494">String</span></span>|  
|<span data-ttu-id="47633-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="47633-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="47633-496">String</span><span class="sxs-lookup"><span data-stu-id="47633-496">String</span></span>|  
|<span data-ttu-id="47633-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-498">String</span><span class="sxs-lookup"><span data-stu-id="47633-498">String</span></span>|  
|<span data-ttu-id="47633-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-499">COLUMN_NAME</span></span>|<span data-ttu-id="47633-500">String</span><span class="sxs-lookup"><span data-stu-id="47633-500">String</span></span>|  
|<span data-ttu-id="47633-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-501">COLUMN_TYPE</span></span>|<span data-ttu-id="47633-502">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-502">Int16</span></span>|  
|<span data-ttu-id="47633-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-503">DATA_TYPE</span></span>|<span data-ttu-id="47633-504">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-504">Int16</span></span>|  
|<span data-ttu-id="47633-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-505">TYPE_NAME</span></span>|<span data-ttu-id="47633-506">String</span><span class="sxs-lookup"><span data-stu-id="47633-506">String</span></span>|  
|<span data-ttu-id="47633-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="47633-507">PRECISION</span></span>|<span data-ttu-id="47633-508">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-508">Int32</span></span>|  
|<span data-ttu-id="47633-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-509">LENGTH</span></span>|<span data-ttu-id="47633-510">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-510">Int32</span></span>|  
|<span data-ttu-id="47633-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="47633-511">SCALE</span></span>|<span data-ttu-id="47633-512">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-512">Int16</span></span>|  
|<span data-ttu-id="47633-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-513">RADIX</span></span>|<span data-ttu-id="47633-514">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-514">Int16</span></span>|  
|<span data-ttu-id="47633-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-515">NULLABLE</span></span>|<span data-ttu-id="47633-516">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-516">Int16</span></span>|  
|<span data-ttu-id="47633-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-517">REMARKS</span></span>|<span data-ttu-id="47633-518">String</span><span class="sxs-lookup"><span data-stu-id="47633-518">String</span></span>|  
|<span data-ttu-id="47633-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="47633-519">OVERLOAD</span></span>|<span data-ttu-id="47633-520">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-520">Int32</span></span>|  
|<span data-ttu-id="47633-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-522">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="47633-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="47633-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="47633-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="47633-524">ColumnName</span></span>|<span data-ttu-id="47633-525">DataType</span><span class="sxs-lookup"><span data-stu-id="47633-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="47633-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="47633-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="47633-527">String</span><span class="sxs-lookup"><span data-stu-id="47633-527">String</span></span>|  
|<span data-ttu-id="47633-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="47633-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="47633-529">String</span><span class="sxs-lookup"><span data-stu-id="47633-529">String</span></span>|  
|<span data-ttu-id="47633-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="47633-531">String</span><span class="sxs-lookup"><span data-stu-id="47633-531">String</span></span>|  
|<span data-ttu-id="47633-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-532">COLUMN_NAME</span></span>|<span data-ttu-id="47633-533">String</span><span class="sxs-lookup"><span data-stu-id="47633-533">String</span></span>|  
|<span data-ttu-id="47633-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-534">COLUMN_TYPE</span></span>|<span data-ttu-id="47633-535">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-535">Int16</span></span>|  
|<span data-ttu-id="47633-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-536">DATA_TYPE</span></span>|<span data-ttu-id="47633-537">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-537">Int16</span></span>|  
|<span data-ttu-id="47633-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="47633-538">TYPE_NAME</span></span>|<span data-ttu-id="47633-539">String</span><span class="sxs-lookup"><span data-stu-id="47633-539">String</span></span>|  
|<span data-ttu-id="47633-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="47633-540">COLUMN_SIZE</span></span>|<span data-ttu-id="47633-541">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-541">Int32</span></span>|  
|<span data-ttu-id="47633-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="47633-543">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-543">Int32</span></span>|  
|<span data-ttu-id="47633-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="47633-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="47633-545">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-545">Int16</span></span>|  
|<span data-ttu-id="47633-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="47633-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="47633-547">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-547">Int16</span></span>|  
|<span data-ttu-id="47633-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-548">NULLABLE</span></span>|<span data-ttu-id="47633-549">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-549">Int16</span></span>|  
|<span data-ttu-id="47633-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="47633-550">REMARKS</span></span>|<span data-ttu-id="47633-551">String</span><span class="sxs-lookup"><span data-stu-id="47633-551">String</span></span>|  
|<span data-ttu-id="47633-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="47633-552">COLUMN_DEF</span></span>|<span data-ttu-id="47633-553">String</span><span class="sxs-lookup"><span data-stu-id="47633-553">String</span></span>|  
|<span data-ttu-id="47633-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="47633-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="47633-555">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-555">Int16</span></span>|  
|<span data-ttu-id="47633-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="47633-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="47633-557">Int16</span><span class="sxs-lookup"><span data-stu-id="47633-557">Int16</span></span>|  
|<span data-ttu-id="47633-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="47633-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="47633-559">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-559">Int32</span></span>|  
|<span data-ttu-id="47633-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="47633-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="47633-561">Int32</span><span class="sxs-lookup"><span data-stu-id="47633-561">Int32</span></span>|  
|<span data-ttu-id="47633-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="47633-562">IS_NULLABLE</span></span>|<span data-ttu-id="47633-563">String</span><span class="sxs-lookup"><span data-stu-id="47633-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47633-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47633-564">See Also</span></span>  
 [<span data-ttu-id="47633-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="47633-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
