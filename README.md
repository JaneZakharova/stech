stech
=====

АСУ сервиса компьютерной техники, есть  возможноть шагалки  по статусам.

Код для продвинутой  шагалки был  написан    чуть  позже.

    function stech_taxar($tid, $act) {
     
      $q = db_select('taxonomy_term_data', 'ttd')
          ->fields('ttd', array('tid', 'name'))
          ->condition('vid', variable_get('stech_status'))
          ->orderBy('weight', 'DESC')
          ->execute();
            
         $arstatus0 = array();
        
         foreach ($q as $rec) {
        
           $arstatus0[$rec->tid] = $rec -> name;
         }
        
          $arstatus = array();
          $arstatus = array_flip($arstatus0);
          $statuskey = array_keys($arstatus0);
 
          $first = array_shift($statuskey);
          $last = end($statuskey); 
         
          switch ($act) {
            case 'next':
                $output = $tid+1; 
                break;
            case "prev":
                 $output = $tid-1; ;
                break;
            case "first":
                $output = $first;
                break;
         
            case "last":
        $output = $last;
        break; 
          }
          return $output;
        }
        
        }}
