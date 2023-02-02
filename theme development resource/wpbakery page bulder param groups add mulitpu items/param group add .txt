<?php
/* human appeal first shorcode create heere now*/

/* */
add_shortcode( 'human_donete_support', 'human_donete_supports' );

function human_donete_supports( $atts ) {
         ob_start();
              $atts = shortcode_atts(array(
                  'box_repeater_items' =>'',        
              ), $atts, 'human_donete_support');

           
              $items = vc_param_group_parse_atts($atts['box_repeater_items']);

      ?>
  

 ?>
            <div class='TopwatchFe'>
                <div class='row'>
                    <?php foreach( $items as $item ) { ?>
                        <div class='col-sm-4'>
                            <div class='TopwatchFe_item'>
                                <h3><?php echo $item['donete_title']; ?></h3>
                                <p>Support our work</p>
                            </div>
                        </div>
                    <?php } ?>
                </div>
            </div>

 		<?php 
}
?>

<?php
add_action( 'vc_before_init', 'human_donete_support_vc' );

function human_donete_support_vc() {
 vc_map([
  "name" => __( "Donete Supports Boxs", "human-appeal" ),
  "base" => "human_donete_support",
  "icon"    => get_template_directory_uri(). '/access/images/logo/logo.png',
  "category" => __( "Human Appleal", "human-appeal"),
  "params" => [
                [
                'type' => 'param_group',
                'param_name' => 'box_repeater_items',
                "icon"    => get_template_directory_uri(). '/access/images/logo/logo.png',
                "category" => __( "Human Appleal", "human-appeal"),
                'params' => [
                                 
                             [
                                  "param_name" => "donete_title",
                                  "type" => "textfield",
                                  "heading" => __("Title", "human-appeal"),
                                  "value" => __("", "human-appeal"),
                              ],
                              [
                                  "param_name" => "descrip",
                                  "type" => "textarea",                            
                                  "heading" => __("Description", "human-appeal"),
                                  "value" => __("", "human-appeal"),
                              ]
                        ]
                ],                    
          ]


    ]);
}
?>