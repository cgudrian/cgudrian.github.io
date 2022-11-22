---
layout: post
title: Finding Trait Implementations in Rust
tags: rust traits
categories: foo bar
---

In Rust things often work while I don't know why. Look at this piece of Rust code:
{% highlight rust %}
fn cursor_test() {
    let buffer = [1, 2, 3];
    let mut cursor = Cursor::new(buffer);
    let value = cursor.get_u8();
    println!("{value}");
}
{% endhighlight %}

The `get_u8` method is defined on the `Buf` trait, so somewhere there has to be
an implementation for this trait for the `Cursor` struct.

This implementation can be found in `buf_impl.rs`:
{% highlight rust %}
impl<T: AsRef<[u8]>> Buf for std::io::Cursor<T> {
        // ...
}
{% endhighlight %}
