`ClangFunctionDifferenceBear <https://github.com/coala-analyzer/coala-bears/tree/master/bears/c_languages/codeclone_detection/ClangFunctionDifferenceBear.py>`_
===============================

Retrieves similarities for code clone detection. Those can be reused in another bear to produce results.
Postprocessing may be done because small functions are less likely to be clones at the same difference value than big functions which may provide a better refactoring opportunity for the user.

`Supported Languages <../README.rst>`_
-----

* C
* C++
* CUDA
* Objective-C
* Objective-C++
* OpenCL
* OpenMP

Settings
--------

+--------------------------+-------------------------------------------------------------+
| Setting                  |  Meaning                                                    |
+==========================+=============================================================+
|                          |                                                             |
| ``average_calculation``  | If set to true the difference calculation function will     |
|                          | take the average of all variable differences as the         |
|                          | difference, else it will normalize the function as a whole  |
|                          | and thus weighting in variables dependent on their size.    |
|                          | (Optional, defaults to 'False'.)                            |
|                          |                                                             |
+--------------------------+-------------------------------------------------------------+
|                          |                                                             |
| ``counting_conditions``  | A comma seperated list of counting conditions. Possible     |
|                          | values are: used, returned, is_condition, in_condition,     |
|                          | in_second_level_condition, in_third_level_condition,        |
|                          | is_assignee, is_assigner, loop_content,                     |
|                          | second_level_loop_content, third_level_loop_content,        |
|                          | is_param, in_sum, in_product, in_binary_operation,          |
|                          | member_accessed. Weightings can be assigned to each         |
|                          | condition due to providing a dict value, i.e. having used   |
|                          | weighted in half as much as other conditions would simply   |
|                          | be: "used: 0.5, is_assignee". Weightings default to 1 if    |
|                          | unset. (Optional, defaults to 'OrderedDict([(<function used |
|                          | at 0x7fefd5312620>, 0.0), (<function returned at            |
|                          | 0x7fefd53126a8>, 1.4), (<function is_condition at           |
|                          | 0x7fefd53127b8>, 0.0), (<function in_condition at           |
|                          | 0x7fefd5312840>, 1.4), (<function in_second_level_condition |
|                          | at 0x7fefd53128c8>, 1.4), (<function                        |
|                          | in_third_level_condition at 0x7fefd5312950>, 1.0),          |
|                          | (<function is_assignee at 0x7fefd53129d8>, 0.0), (<function |
|                          | is_assigner at 0x7fefd5312a60>, 0.6), (<function            |
|                          | loop_content at 0x7fefd5312b70>, 0.0), (<function           |
|                          | second_level_loop_content at 0x7fefd5312bf8>, 1),           |
|                          | (<function third_level_loop_content at 0x7fefd5312c80>, 1), |
|                          | (<function is_param at 0x7fefd5312d08>, 2.0), (<function    |
|                          | is_called at 0x7fefd5312d90>, 1.4), (<function              |
|                          | is_call_param at 0x7fefd5312e18>, 0.0), (<function in_sum   |
|                          | at 0x7fefd5312400>, 2.0), (<function in_product at          |
|                          | 0x7fefd5312488>, 0.0), (<function in_binary_operation at    |
|                          | 0x7fefd5312510>, 1), (<function member_accessed at          |
|                          | 0x7fefd5312598>, 1)])'.)                                    |
|                          |                                                             |
+--------------------------+-------------------------------------------------------------+
|                          |                                                             |
| ``exp_postprocessing``   | If set to true, the difference value of big function pairs  |
|                          | will be reduced using an exponential approach. (Optional,   |
|                          | defaults to 'False'.)                                       |
|                          |                                                             |
+--------------------------+-------------------------------------------------------------+
|                          |                                                             |
| ``extra_include_paths``  | A list containing additional include paths. (Optional,      |
|                          | defaults to '()'.)                                          |
|                          |                                                             |
+--------------------------+-------------------------------------------------------------+
|                          |                                                             |
| ``poly_postprocessing``  | If set to true, the difference value of big function pairs  |
|                          | will be reduced using a polynomial approach. (Optional,     |
|                          | defaults to 'True'.)                                        |
|                          |                                                             |
+--------------------------+-------------------------------------------------------------+
