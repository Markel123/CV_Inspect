### ð åå­ç®¡ç
C++åå­åä¸ºä»£ç åºåæ°æ®åº(å¸¸éåºãéæ/å¨å±å­å¨åº<ä¸¤èå¨ä¸åå¿>ãå åºãæ åº)ï¼ä»£ç åºåå¸¸éåºä¸ºåªè¯»ï¼åå ä¸ªä¸ºå¯è¯»å  
- ä»£ç åºï¼å­æ¾å¯æ§è¡çæºå¨æä»¤  
- å¸¸éåºï¼å­æ¾å¸¸éï¼æ¯å¦constå³é®å­éå®çå¸¸åéãå­ç¬¦ä¸²å­é¢å¼  
- éæ/å¨å±å­å¨åºï¼éæå­å¨åºåå¨å±å­å¨åºæ¯ä¸èµ·çï¼éæå¨å±åéåå¨å±åéçå¯ä¸åºå«çä½ç¨åï¼éæå¨å±åéåªè½ä½ç¨äºæå¨çæä»¶ï¼å¨å±åéå¯ä»¥éè¿externå³é®å­è¢«å¶ä»æä»¶ä½¿ç¨  
- å åºï¼ç¨åºåä½¿ç¨mallocå½æ°åå»ºçå­å¨åºï¼éè¦ä½¿ç¨å¯¹åºçdeleteå½æ°å é¤ï¼å¦åä¼åå­æ³æ¼  
- æ åºï¼å­æ¾å±é¨åéï¼ç±ç¨åºèªå¨åå»ºåéæ¯
### ð æ©å±åç¤ºä¾
#### ðéæå±é¨åéä¸å¸¸é
- éæå±é¨åéï¼åªæå½å¶æå¨å½æ°è¢«æ§è¡ï¼å®æä¼è¢«ä½¿ç¨ï¼å¹¶ä¸åªä¼åå§åä¸æ¬¡ï¼åé¢è°ç¨æ¶ï¼é½æ¯ä½¿ç¨åä¸æ¬¡çå¼ï¼ä¸éæå¨å±åéçåºå«åªæä½ç¨åä¸å(å¨å±/å±é¨)ï¼é½æ¯å­å¨éæåº  
- å¸¸éï¼å­ç¬¦ä¸²å¸¸éï¼ä¾å¦"abcdf"ï¼å­å¨å¨å¸¸éåºï¼ä»¥ä¸ä¸¤ç§æåµï¼  
  >1.`char* p="abcde"`,å°æéåépæåå­ç¬¦ä¸²  
  >2.`char pp[]="abcde"`ï¼æ è®ºppæ¯å¨å±åé(å¨å±åº)è¿æ¯å±é¨åé(æ åº)ï¼é½å¼è¾ç©ºé´ç»ppï¼å°å­ç¬¦ä¸²å¤å¶è¿å»  
#### ðåå­å¯¹é½
æ³è¦æ¸æ¥C++ç¨åºå ç¨å¤å°åå­ï¼éè¦ç¥éC++æ¯å¦ä½è¿è¡åå­ç®¡çç  
- 1.ä»£ç ãå¨å±åéãéæåéãå¸¸éç§°ä¸ºåºå®é¨åï¼å¶åå­æ¶èæ¯ä¸ä¼éçä»£ç è¿è¡èæ¹åç  
- 2.æ ä¸çå½æ°å½¢åãå±é¨åéã*å½æ°è¿åå¼*ï¼å ä¸çç¨åºååéçåå­ç§°ä¸ºå¯åé¨åï¼å¶åå­æ¶èä¼éçä»£ç è¿è¡èå¨æååï¼åå­æ³æ¼éå¸¸ä¸ºå åå­æ³æ¼  
- 3.è®¡ç®ç¨åºå ç¨çåå­å¤§å°ï¼éè¦ç¥éä»ä¹æ¯åå­å¯¹é½ï¼CPUè¯»åæ°æ®æ¯ä»¥ç¼å­è¡(cacheline)ä¸ºåä½è¯»åçï¼ä¸è¬cachelineå¤§å°ä¸º64å­èï¼ä¹å°±æ¯è¯´CPUä¸æ¬¡ä¼è¯»å64å­èçæ°æ®ã  

```
struct myStr{  
  char x1;  
  int x2;  
}
```  

`éåå­å¯¹é½ç:`  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|----|----|----|----|----|----|----|----|----|
| char | int[0] | int[1] | int[2] | int[3] |  |  |  |

`åå­å¯¹é½ç:`  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|----|----|----|----|----|----|----|----|----|
| char |  |  |  |  |int[0] | int[1] | int[2] | int[3] |  

åè®¾cachelineå¤§å°æ¯4å­èï¼intçå¤§å°æ¯4å­èï¼CPUå¯»åä»charå¼å§;int[i]è¡¨ç¤ºintååéçç¬¬iä¸ªå­è
>1.éå¯¹é½ï¼ç¬¬ä¸æ¬¡è¯»åå° charãint[0]ãint[1]ãint[2]ãç¬¬äºæ¬¡è¯»åå°int[3]ã ã ã ãï¼ç¶åå°ä¸¤æ¬¡è¯»åçåå®¹åå¹¶æè½å¾å°å®æ´çint  
>2.å¯¹é½ï¼ç¬¬ä¸å°±å¯ä»¥è¯»åå°å®æ´çint  
åå­å¯¹é½è½ç¶ä¼å¤å åå­ï¼ä½æ¯ç¸å¯¹äºéåº¦æåæ¥è¯´ï¼çºç²å¾å°
