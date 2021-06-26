```void IF(){
  int ifbegin = nextLabel();
  int ifend = nextLabel();
  int ifmid = nextLabel();
  emit("(L%d)\n", ifbegin);
  skip("if");
  skip("(");
  int e = E();
  emit("if not t%d goto L%d\n", e, ifmid);
  skip(")");
  STMT();
  emit("goto L%d\n", ifend);
  emit("(L%d)\n", ifmid);
  if(isNext("else")){
    skip("else");
    STMT();
    emit("(L%d)\n", ifend);
``` 