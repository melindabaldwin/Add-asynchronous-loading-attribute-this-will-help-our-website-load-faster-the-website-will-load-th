# Add-asynchronous-loading-attribute-this-will-help-our-website-load-faster-the-website-will-load-th
Add asynchronous loading attribute, this will help our website load faster, the website will load the content and css first, then load the script. Here are two code snippets to help asynchronously load, but the way of writing is different, you only use one of the two, each // sign is a paragraph.
// Asynchronous load JS
function defer_parsing_of_js ( $url ) {
    if ( FALSE === strpos( $url, '.js' ) ) return $url;
    return "$url' async defer='defer";
}
add_filter( 'clean_url', 'defer_parsing_of_js', 11, 1 );

// Asynchronous load JS
function async_js($tag){
$scripts_to_async = array('jquery.js', 'jquery-migrate.min.js');
foreach($scripts_to_async as $async_script){
    if(true == strpos($tag, $async_script ) )
    return str_replace(' src', ' async="async" src', $tag);    
}
return $tag;
}
add_filter( 'script_loader_tag', 'async_js', 10);
