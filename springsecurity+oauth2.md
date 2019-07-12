配置好了以后无法验证。并在idle报There is no PasswordEncoder mapped for the id "null"：
是因为springbootsecurity5升级后使用了加密方式。
需要加上

public class CustomPasswordEncoder implements PasswordEncoder {

    @Override
    public String encode(CharSequence charSequence) {
        return charSequence.toString();
    }

    @Override
    public boolean matches(CharSequence charSequence, String s) {
        return s.equals(charSequence.toString());
    }
}


在用户认证规则中添加自定义的 PasswordEncoder 实例，具体内容如下：

    // 自定义配置认证规则
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
                .withUser("zhangsan").password("12345").roles("SuperAdmin")
                .and()
                .withUser("lisi").password("12345").roles("Admin")
                .and()
                .withUser("wangwu").password("12345").roles("Employee")
                .and()
                .passwordEncoder(new CustomPasswordEncoder())

    }
--------------------- 
作者：csdn-华仔 
来源：CSDN 
原文：https://blog.csdn.net/Hello_World_QWP/article/details/81811462 
版权声明：本文为博主原创文章，转载请附上博文链接！


--
