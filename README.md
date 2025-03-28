# genetic-trait-simulator
import java.util.*;
        public class Factorial {
            public static void main(String[] args) {
                Scanner in = new Scanner(System.in);
                int n, option, i;
                System.out.println("enter the number of traits");
                n = in.nextInt();
                int p = (int) Math.pow(2, n);
                String[] q = new String[n];
                String[] m = new String[n];
                String ab = " ";
                String mq = " ";
                char[] a = new char[p];
                char[] b = new char[p];
                String[] g = new String[n];
                char ax, bx;
                for (i = 0; i < n; ++i) {
                    System.out.println("enter the characteristic");
                    g[i] = in.next();
                    System.out.println("enter the dominant trait");
                    m[i] = in.next();
                    System.out.println("enter the recessive trait");
                    q[i] = in.next();
                    System.out.println("Enter a symbol for dominant trait ");
                    ax = in.next().charAt(0);
                    a[i] = Character.toUpperCase(ax);
                    System.out.println("Enter the symbol for recessive trait");
                    bx = in.next().charAt(0);
                    b[i] = Character.toLowerCase(bx);
                    System.out.println("trait set " + (i + 1) + " of " + g[i]);
                }
                System.out.println("all possible outcomes= " + Math.pow(2, n));
                System.out.println("choose any of the option below");
                System.out.println(" 1: any one random gene combination");
                System.out.println(" 2: all possible variations");
                System.out.println("enter your choice");
                option = in.nextInt();
                if (option == 1) {
                    for (i = 0; i < n; i++) {
                        double d = Math.random() * 2;
                        int random = (int) d;
                        if (random == 1) {
                            ab = ab.concat(String.valueOf(a[i]));
                            mq = mq.concat(m[i]) + ", ";
                        }
                        if (random == 0) {
                            ab = ab.concat(String.valueOf(b[i]));
                            mq = mq.concat(q[i]) + ", ";
                        }
                    }
                    System.out.println("random variation of gene= " + ab);
                    System.out.println("word format= " + mq);
                }
                if (option == 2) {
                    String[] s = new String[p * n];
                    String[] ss = new String[p * n];
                    String[] sn = new String[p * n];
                    String[] snn = new String[p * n];
                    int k = 0;
                    if (n == 2) {
                        do {
                            for (i = 0; i < n; i++) {
                                double d = Math.random() * 2;
                                int random = ((int) d) + 1;
                                if (random == 1) {
                                    ab = ab.concat(String.valueOf(a[i]));
                                    mq = mq.concat(m[i]) + ", ";
                                }
                                if (random == 2) {
                                    ab = ab.concat(String.valueOf(b[i]));
                                    mq = mq.concat(q[i]) + ", ";
                                }
                            }
                            s[k] = ab;
                            ss[k] = mq;

                            if (k >= 3) {
                                if (s[k].equals(s[k - 1]) || s[k].equals(s[0]) || s[k].equals(s[1])|| s[k].equals(s[k-2])) {
                                    ab = "";
                                    mq = "";
                                } else {
                                    ab = "";
                                    mq = "";
                                    sn[k] = s[k];
                                    snn[k] = ss[k];
                                    k++;
                                }
                            }
                            else if (k < 3) {
                                if (k != 0 && s[k].equals(s[k - 1]) || k != 0 && s[k].equals(s[0])){
                                    ab = "";
                                    mq = "";
                                } else {
                                    ab = "";
                                    mq = "";
                                    sn[k] = s[k];
                                    snn[k] = ss[k];
                                    k++;
                                }
                            }
                        } while (k != p);
                        for (k = 0; k < p; k++)
                            System.out.println(sn[k] + " = " + snn[k]);
                    }

                }
            }
        }
