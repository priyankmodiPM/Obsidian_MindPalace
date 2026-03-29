Parent - [[Auto-Reflow MOC]]

#### Description
The idea here is to check how performant the service is and if the end to end pipeline works as expected.
---

| S.No. | Topic                                                                                          | Approach                                                                   | Status                                    |
| ----- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ----------------------------------------- |
| 1.    | Check if **AutoReflow** service is performant (100 concurrent requests)                        | - send multiple queries to service                                         | <input type="checkbox" checked id="00">   |
| 2.    | Check if **Aesthetiq** service is performant (100 concurrent requests)                         | - SSH to instance<br>- send multiple queries to aeshetiq internal endpoint | <input type="checkbox" unchecked id="00"> |
| 3.    | Check the problems with current service                                                        | - Why do requests fail. Check logs                                         | <input type="checkbox" unchecked id="00"> |
| 3.    | Try with token cache enabled                                                                   |                                                                            | <input type="checkbox" unchecked id="00"> |
| 4.    | Try with s3 url cache enabled                                                                  |                                                                            | <input type="checkbox" unchecked id="00"> |
| 5.    | Fix image sizes, for original template url and other images to match exactly the expected size |                                                                            |                                           |
| 6.    | Check that background image or coloredbackgroud is handled well in all cases                   |                                                                            |                                           |
| 7.    | Check if logs look ok                                                                          |                                                                            | <input type="checkbox" unchecked id="00"> |


| S.no.           | Test        | env   | Number | Result  | Errors              |
| --------------- | ----------- | ----- | ------ | ------- | ------------------- |
| 1.              | /sleep-test | local | 100    | ✅ OK    |                     |
| 2.              | /sleep-test | stage | 100    |         |                     |
| 3.              | /variant    | local | 20     | ❌ 0/20  | Timeout out         |
| 4.              | /variant    | local | 10     | ❌ 0/20  |                     |
| 5.              | /variant    | local | 4      | ✅ 4/4   |                     |
| 6.              | /variant    | local | 10     | ❌ 3/10  | 410: Polling failed |
| 7.              | /variant    | stage | 10     | ❌ 1/10  | 504: Timed out      |
| 8.              | /variant    | stage | 4      | ✅ 4/4   |                     |
| Change on local |             |       |        |         |                     |
| 9.              | /variant    | local | 10     | ✅ 9/10  |                     |
| 10.             | /variant    | local | 10     | ✅ 10/10 |                     |
