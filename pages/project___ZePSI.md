query-table:: true
#+BEGIN_QUERY
{:title "TODOs in this project"
:query [:find (pull ?b [*])
         :where
         [?b :block/refs ?p]
         [?p :block/name "project/zepsi"]
         [?b :block/marker ?m]
         [(contains? #{"TODO" "DOING" "NOW"} ?m)]]
 :result-transform (fn [result]
                     (sort-by (fn [h]
                                (get h :block/created-at))
                              result))
 :collapsed? false}
#+END_QUERY
#+BEGIN_QUERY
{:query [:find (pull ?b [*])
         :where
         [?p :block/name "project/zepsi"]
         [?parent :block/refs ?p]
         [?b :block/parent ?parent]
         [?b :block/marker ?marker]
         [(contains? #{"TODO" "DOING" "NOW"} ?marker)]]
 :collapsed? false}
#+END_QUERY

-
-
- TODO Simulate Q-band single crystal trEPR
  project:: [[project/ZePSI]]
- DONE Shorten measurement time for oop vs beta
- DONE Include phase shift correction in python script
- DONE Include MPFU amplitude to B1 calibration curve in python script
- TODO Deal with averaging of fast oscillating out of diagonal terms
  project:: [[project/ZePSI]]
-