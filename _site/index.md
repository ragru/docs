# Header 1
## Header 2

親譲りの無鉄砲で小供の時から損ばかりしている。小学校に居る時分学校の二階から飛び降りて一週間ほど腰を抜かした事がある。なぜそんな無闇をしたと聞く人があるかも知れぬ。別段深い理由でもない。新築の二階から首を出していたら、同級生の一人が冗談に、いくら威張っても、そこから飛び降りる事は出来まい。弱虫やーい。と囃したからである。小使に負ぶさって帰って来た時、おやじが大きな眼をして二階ぐらいから飛び降りて腰を抜かす奴があるかと云ったから、この次は抜かさずに飛んで見せますと答えた。（青空文庫より）

### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

```ruby
  def prev_to(record):
    if record.is_a?(Article)
      articles = self
      if articles.includes_values.present?
        articles = articles.unscope(:includes).left_outer_joins(*self.includes_values)
      end
      subq = articles.select(:id).group('articles.id').to_sql
      sql = "SELECT id, lag FROM (SELECT id, lag(id) over() FROM (#{subq}) a) l WHERE l.id = ?"
      rec = Article.find_by_sql([sql, record.id])
      Article.find(rec.first[:lag]) rescue nil
    else
      raise '"ActiveRecord::Relation#prev_to" supports articles only.'
    end
  end
```
