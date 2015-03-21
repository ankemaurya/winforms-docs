---
title: Adding and Removing Nodes
page_title: Adding and Removing Nodes
description: Adding and Removing Nodes
slug: treeview-working-with-nodes-adding-and-removing-nodes
tags: adding,and,removing,nodes
published: True
position: 0
---

# Adding and Removing Nodes



## Adding Nodes

RadTreeView nodes are arranged in a hierarchical structure. To add a node to the first level in a
          __RadTreeView__ use the __Nodes.Add()__ method. To add a
          child node to another node use the parent nodes __Nodes.Add()__ method.
          __Nodes.Add()__places the node at the end of the __Nodes__ collection. 
          You may also use __Nodes.Insert()__ to place the node anywhere in the __Nodes__
          collection.
        

The following example demonstrates how to add nodes using code:
        

#### __[C#]__

{{region addNodes}}
	        private void AddNodes()
	        {
	            RadTreeNode Node1 = new RadTreeNode("Node1");
	            Node1.Tag = 1234;
	            Node1.BackColor = Color.Blue;
	            RadTreeNode Node2 = new RadTreeNode("Node2");
	            RadTreeNode Node3 = new RadTreeNode("Node3");
	            RadTreeNode Node4 = new RadTreeNode("Node4");
	            radTreeView1.Nodes.Add(Node1);
	            radTreeView1.Nodes.Add(Node2);
	            Node1.Nodes.Add(Node3);
	            Node2.Nodes.Add(Node4);
	            //Alternative methods for adding nodes
	            //RadTreeNode Node1 = radTreeView1.Nodes.Add("Node1");
	            //RadTreeNode Node2 = radTreeView1.Nodes.Add("Node2");
	            //Node1.Nodes.Add("Node3");
	            //Node2.Nodes.Add("Node4");
	        }
	{{endregion}}



#### __[VB.NET]__

{{region addNodes}}
	    Private Sub AddNodes()
	        Dim Node1 As New RadTreeNode("Node1")
	        Node1.Tag = 1234
	        Node1.BackColor = Color.Blue
	        Dim Node2 As New RadTreeNode("Node2")
	        Dim Node3 As New RadTreeNode("Node3")
	        Dim Node4 As New RadTreeNode("Node4")
	        RadTreeView1.Nodes.Add(Node1)
	        RadTreeView1.Nodes.Add(Node2)
	        Node1.Nodes.Add(Node3)
	        Node2.Nodes.Add(Node4)
	        'Alternative methods for adding nodes
	        'RadTreeNode Node1 = radTreeView1.Nodes.Add("Node1");
	        'RadTreeNode Node2 = radTreeView1.Nodes.Add("Node2");
	        'Node1.Nodes.Add("Node3");
	        'Node2.Nodes.Add("Node4");
	    End Sub
	    '#End Region
	
	    '#Region removeNodes
	    Private Sub RemoveNodes()
	        'Remove a single node
	        RadTreeView1.Nodes(0).Remove()
	        ' removes all nodes from TreeView
	        RadTreeView1.Nodes.Clear()
	    End Sub
	    '#End Region
	End Class



Just before a node is added, the  __NodeAdding__ event is fired. The event arguments of this event allow
          you to cancel the adding of the node. If the operation was not canceled, then the node will be added to the RadTreeView and
          the  __NodeAdded__ event will be fired. The following code snippet demonstrates the usage of these events:
        

#### __[C#]__

{{region NodeAdding}}
	
	        void radTreeView1_NodeAdding(object sender, RadTreeViewCancelEventArgs e)
	        {
	            if (e.Node.Text.Contains("Non-insertable"))
	            {
	                e.Cancel = true;
	            }
	        }
	
	        void radTreeView1_NodeAdded(object sender, RadTreeViewEventArgs e)
	        {
	            RadMessageBox.Show("Node {" + e.Node.Text + "} was added");
	        }
	
	{{endregion}}



#### __[VB.NET]__

{{region NodeAdding}}
	
	    Private Sub RadTreeView1_NodeAdding(sender As Object, e As RadTreeViewCancelEventArgs) Handles RadTreeView1.NodeAdding
	        If e.Node.Text.Contains("Non-insertable") Then
	            e.Cancel = True
	        End If
	    End Sub
	
	    Private Sub RadTreeView1_NodeAdded(sender As Object, e As RadTreeViewEventArgs) Handles RadTreeView1.NodeAdded
	        RadMessageBox.Show("Node {" + e.Node.Text + "} was added")
	    End Sub
	
	#End Region
	
	#Region "NodeRemoving"
	
	    Private Sub RadTreeView1_NodeRemoving(sender As Object, e As RadTreeViewCancelEventArgs) Handles RadTreeView1.NodeRemoving
	        If e.Node.Text.Contains("Unremovable") Then
	            e.Cancel = True
	        End If
	    End Sub
	
	    Private Sub RadTreeView1_NodeRemoved(sender As Object, e As RadTreeViewEventArgs) Handles RadTreeView1.NodeRemoved
	        RadMessageBox.Show("Node {" + e.Node.Text + "} was removed")
	    End Sub
	
	#End Region
	
	    Private Sub InsertingNodes()
	        '#Region insertingNodes
	        ' Create two parent nodes
	        Dim parentNode1 As New RadTreeNode("First Parent")
	        Dim parentNode2 As New RadTreeNode("Second Parent")
	        ' Add the parent nodes to tree view's nodes collection
	        Me.RadTreeView1.Nodes.Add(parentNode1)
	        Me.RadTreeView1.Nodes.Add(parentNode2)
	        ' Create child nodes
	        Dim childNode As New RadTreeNode("Child Node")
	        Dim childNode2 As New RadTreeNode("Child Node2")
	        Dim childNode3 As New RadTreeNode("Child Node3")
	        Dim childNode4 As New RadTreeNode("Child Node4")
	        Dim childNode5 As New RadTreeNode("Child Node5")
	        ' Add a single child node to the parentNode1 nodes collection and
	        ' multiple nodes to the parentNode2 nodes collection
	        parentNode1.Nodes.Add(childNode)
	        parentNode2.Nodes.Add(childNode2)
	        parentNode2.Nodes.Add(childNode3)
	        parentNode2.Nodes.Add(childNode4)
	        parentNode2.Nodes.Add(childNode5)
	        ' Insert the childNode instance to the parentNode2 nodes collection
	        parentNode2.Nodes.Insert(1, childNode)
	        '#End Region
	    End Sub
	
	    Private Sub OptionList()
	        '#Region optionList
	        Dim Node1 As New RadTreeNode("Node1")
	        Node1.Expanded = True
	        Node1.CheckType = ChildListType.OptionList
	        Dim Node2 As New RadTreeNode("Node2")
	        Dim Node3 As New RadTreeNode("Node3")
	        Dim Node4 As New RadTreeNode("Node4")
	        RadTreeView1.Nodes.Add(Node1)
	        RadTreeView1.Nodes.Add(Node2)
	        Node1.Nodes.Add(Node3)
	        Node1.Nodes.Add(Node4)
	        '#End Region
	    End Sub
	
	    '#Region doubleClick
	    Private Sub radTreeView1_DoubleClick(ByVal sender As Object, ByVal e As EventArgs)
	        Dim args As MouseEventArgs = TryCast(e, MouseEventArgs)
	        Dim clickedNode As RadTreeNode = RadTreeView1.GetNodeAt(args.X, args.Y)
	        If clickedNode IsNot Nothing Then
	            MessageBox.Show("Node Text: " & clickedNode.Text & "  Node Value: " & clickedNode.Tag)
	        End If
	    End Sub
	    '#End Region
	
	    '#Region addNodes
	    Private Sub AddNodes()
	        Dim Node1 As New RadTreeNode("Node1")
	        Node1.Tag = 1234
	        Node1.BackColor = Color.Blue
	        Dim Node2 As New RadTreeNode("Node2")
	        Dim Node3 As New RadTreeNode("Node3")
	        Dim Node4 As New RadTreeNode("Node4")
	        RadTreeView1.Nodes.Add(Node1)
	        RadTreeView1.Nodes.Add(Node2)
	        Node1.Nodes.Add(Node3)
	        Node2.Nodes.Add(Node4)
	        'Alternative methods for adding nodes
	        'RadTreeNode Node1 = radTreeView1.Nodes.Add("Node1");
	        'RadTreeNode Node2 = radTreeView1.Nodes.Add("Node2");
	        'Node1.Nodes.Add("Node3");
	        'Node2.Nodes.Add("Node4");
	    End Sub
	    '#End Region
	
	    '#Region removeNodes
	    Private Sub RemoveNodes()
	        'Remove a single node
	        RadTreeView1.Nodes(0).Remove()
	        ' removes all nodes from TreeView
	        RadTreeView1.Nodes.Clear()
	    End Sub
	    '#End Region
	End Class



## Removing Nodes

To remove a single node use the __Remove()__ method of the node. To remove *all *nodes of the RadTreeView use the __Nodes.Clear()__ method__.__

#### __[C#]__

{{region removeNodes}}
	        private void RemoveNodes()
	        {
	            //Remove a single node
	            radTreeView1.Nodes[0].Remove();
	            // removes all nodes from TreeView
	            radTreeView1.Nodes.Clear();
	        }
	{{endregion}}



#### __[VB.NET]__

{{region removeNodes}}
	    Private Sub RemoveNodes()
	        'Remove a single node
	        RadTreeView1.Nodes(0).Remove()
	        ' removes all nodes from TreeView
	        RadTreeView1.Nodes.Clear()
	    End Sub
	    '#End Region
	End Class



Just before a node is removed, the __NodeRemoving__ event is fired. The event arguments of this event allow you to
          cancel the remove operation. If the operation was not canceled, then the node will be removed from RadTreeView and the __NodeRemoved__
          event will be fired. The following code snippet demonstrates the usage of these events:
        

#### __[C#]__

{{region NodeRemoving}}
	
	        void radTreeView1_NodeRemoving(object sender, RadTreeViewCancelEventArgs e)
	        {
	            if (e.Node.Text.Contains("Unremovable"))
	            {
	                e.Cancel = true;
	            }
	        }
	
	        void radTreeView1_NodeRemoved(object sender, RadTreeViewEventArgs e)
	        {
	            RadMessageBox.Show("Node {" + e.Node.Text + "} was removed");
	        }
	
	{{endregion}}



#### __[VB.NET]__

{{region NodeRemoving}}
	
	    Private Sub RadTreeView1_NodeRemoving(sender As Object, e As RadTreeViewCancelEventArgs) Handles RadTreeView1.NodeRemoving
	        If e.Node.Text.Contains("Unremovable") Then
	            e.Cancel = True
	        End If
	    End Sub
	
	    Private Sub RadTreeView1_NodeRemoved(sender As Object, e As RadTreeViewEventArgs) Handles RadTreeView1.NodeRemoved
	        RadMessageBox.Show("Node {" + e.Node.Text + "} was removed")
	    End Sub
	
	#End Region
	
	    Private Sub InsertingNodes()
	        '#Region insertingNodes
	        ' Create two parent nodes
	        Dim parentNode1 As New RadTreeNode("First Parent")
	        Dim parentNode2 As New RadTreeNode("Second Parent")
	        ' Add the parent nodes to tree view's nodes collection
	        Me.RadTreeView1.Nodes.Add(parentNode1)
	        Me.RadTreeView1.Nodes.Add(parentNode2)
	        ' Create child nodes
	        Dim childNode As New RadTreeNode("Child Node")
	        Dim childNode2 As New RadTreeNode("Child Node2")
	        Dim childNode3 As New RadTreeNode("Child Node3")
	        Dim childNode4 As New RadTreeNode("Child Node4")
	        Dim childNode5 As New RadTreeNode("Child Node5")
	        ' Add a single child node to the parentNode1 nodes collection and
	        ' multiple nodes to the parentNode2 nodes collection
	        parentNode1.Nodes.Add(childNode)
	        parentNode2.Nodes.Add(childNode2)
	        parentNode2.Nodes.Add(childNode3)
	        parentNode2.Nodes.Add(childNode4)
	        parentNode2.Nodes.Add(childNode5)
	        ' Insert the childNode instance to the parentNode2 nodes collection
	        parentNode2.Nodes.Insert(1, childNode)
	        '#End Region
	    End Sub
	
	    Private Sub OptionList()
	        '#Region optionList
	        Dim Node1 As New RadTreeNode("Node1")
	        Node1.Expanded = True
	        Node1.CheckType = ChildListType.OptionList
	        Dim Node2 As New RadTreeNode("Node2")
	        Dim Node3 As New RadTreeNode("Node3")
	        Dim Node4 As New RadTreeNode("Node4")
	        RadTreeView1.Nodes.Add(Node1)
	        RadTreeView1.Nodes.Add(Node2)
	        Node1.Nodes.Add(Node3)
	        Node1.Nodes.Add(Node4)
	        '#End Region
	    End Sub
	
	    '#Region doubleClick
	    Private Sub radTreeView1_DoubleClick(ByVal sender As Object, ByVal e As EventArgs)
	        Dim args As MouseEventArgs = TryCast(e, MouseEventArgs)
	        Dim clickedNode As RadTreeNode = RadTreeView1.GetNodeAt(args.X, args.Y)
	        If clickedNode IsNot Nothing Then
	            MessageBox.Show("Node Text: " & clickedNode.Text & "  Node Value: " & clickedNode.Tag)
	        End If
	    End Sub
	    '#End Region
	
	    '#Region addNodes
	    Private Sub AddNodes()
	        Dim Node1 As New RadTreeNode("Node1")
	        Node1.Tag = 1234
	        Node1.BackColor = Color.Blue
	        Dim Node2 As New RadTreeNode("Node2")
	        Dim Node3 As New RadTreeNode("Node3")
	        Dim Node4 As New RadTreeNode("Node4")
	        RadTreeView1.Nodes.Add(Node1)
	        RadTreeView1.Nodes.Add(Node2)
	        Node1.Nodes.Add(Node3)
	        Node2.Nodes.Add(Node4)
	        'Alternative methods for adding nodes
	        'RadTreeNode Node1 = radTreeView1.Nodes.Add("Node1");
	        'RadTreeNode Node2 = radTreeView1.Nodes.Add("Node2");
	        'Node1.Nodes.Add("Node3");
	        'Node2.Nodes.Add("Node4");
	    End Sub
	    '#End Region
	
	    '#Region removeNodes
	    Private Sub RemoveNodes()
	        'Remove a single node
	        RadTreeView1.Nodes(0).Remove()
	        ' removes all nodes from TreeView
	        RadTreeView1.Nodes.Clear()
	    End Sub
	    '#End Region
	End Class

